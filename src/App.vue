<template>
  <site-header></site-header>
  <theme-control v-on:change-theme="updateTheme"></theme-control>
  <transition>
    <router-view />
  </transition>
</template>

<script>
import SiteHeader from "./components/SiteHeader.vue";
import ThemeControl from "./components/ThemeControl.vue";

let pageHtml = document.querySelector("html");

export default {
  components: {
    SiteHeader,
    ThemeControl,
  },

  data() {
    return {
      pageHtml,
    };
  },

  methods: {
    updateTheme({ currentTheme, themes }) {
      let { mode, theme } = currentTheme;
      console.log(mode, theme);
      mode.active
        ? pageHtml.classList.add(mode.name)
        : pageHtml.classList.remove(mode.name);

      console.log(themes)


      themes.forEach(x => {
        pageHtml.classList.remove(x.name);
      });
      let activeTheme = themes.find(x => {
        console.log(x.name, theme.name)
        return x.name === theme.name
      });
      pageHtml.classList.add(activeTheme.name)

      console.log(activeTheme);
    },
  },

  mounted() {
    this.pageHtml = document.querySelector("html");
    console.log(pageHtml);
  },
};
</script>

<style lang="scss">
// import main scss file which conatins all external stylesheet and custom utility classes
@import "@/scss/main.scss";

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100vh;
  background: var(--bg-2);

  // apply the following styles to all elements under #app
  * {
    transition: all 0.32s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  }
}

// wa-trans style rule
[data-wa-trans="wrapper"] {
  // for loop to generate multiple :nth-child(n) rules
  @for $n from 0 through 5 {
    // apply a transition delay based on the value of $n
    // this applies to children of data-wa-trans="wrapper" with the attribute data-wa-trans="child"
    // <element data-wa-trans="wrapper">
    //  <element data-wa-trans="child" :nth-child>   << applies to this element
    //  <element :nth-child>   << does not apply to this element
    [data-wa-trans="child"]:nth-child(#{$n}) {
      // i.e if n=0
      // transition-duration: 0.32s + 0/4 === 0.32s
      // transition-duration: 0.32s + 1/4 === 0.32s + 0.25 === 0.57s
      transition-duration: 0.32s + $n / 4 !important;
    }

    // apply a transition delay based on the value of $n
    // this applies to children of data-wa-trans="wrapper" with the attribute data-wa-dur="n"
    [data-wa-dur="#{$n}"] {
      transition-duration: 0.32s + $n !important;
    }
  }
}

// applies when element is entering
.v-enter-active {
  transition-duration: 1s !important;
}

// applies when element is leaving
.v-leave-active {
  transition-duration: 2s !important;
}

// applies befor element has entered, and left
.v-enter-from,
.v-leave-to {
  opacity: 0;

  // applies to children of <transition> === #app with attributes data-wa-trans & data-wa-dur
  [data-wa-trans="child"],
  [data-wa-dur] {
    opacity: 0;
    transform: translateY(100px);
  }
}
</style>
