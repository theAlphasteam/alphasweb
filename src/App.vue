<template>
  <site-header></site-header>
  <transition>
    <router-view />
  </transition>
</template>

<script>
import SiteHeader from "./components/SiteHeader.vue";

export default {
  components: {
    SiteHeader,
  },
};
</script>

<style lang="scss">
@import "@/scss/main.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  overflow-x: hidden;
  min-height: 100vh;
  background: var(--bg-2);

  * {
    transition: all 0.32s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  }
}

[data-wa-trans="wrapper"] {
  @for $count from 0 through 5 {
    [data-wa-trans="child"]:nth-child(#{$count}) {
      transition-duration: 0.32s + $count / 4 !important;
    }

    [data-wa-dur="#{$count}"] {
      transition-duration: 0.32s + $count !important;
    }
  }
}

.v-enter-active {
  transition-duration: 1s !important;
}
.v-leave-active {
  transition-duration: 2s !important;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;

  [data-wa-trans="child"],
  [data-wa-dur] {
    opacity: 0;
    transform: translateY(100px);
  }
}
</style>
