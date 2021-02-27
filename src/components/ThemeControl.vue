<template>
  <div class="theme-control__cont glass glass--bg">
    <ul class="modes theme-control__group">
      <li
        class="modes__mode theme-control__opt"
        v-for="(mode, i) in themes.modes"
        v-bind:key="i"
        :title="mode.name"
        :style="{ 'background-color': mode.color }"
        @click="changeTheme({ mode: mode.name })"
      >
        {{ mode.icon[activeIndex] }}
      </li>
    </ul>
    <ul class="theme-control__group themes">
      <li
        class="themes__theme theme-control__opt"
        v-for="(theme, i) in themes.themes"
        :key="i"
        :title="theme.name"
        :style="{ 'background-color': theme.color }"
        @click="changeTheme({ theme: theme.name })"
      ></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ThemeControl",
  data() {
    return {
      themes: {
        modes: [
          {
            name: "dark",
            color: "var(--dark)",
            icon: ["🌙", "🌞"],
          },
        ],

        themes: [
          {
            name: "blue",
            color: "var(--blue)",
          },
          {
            name: "purple",
            color: "var(--purple)",
          },
        ],
      },

      currentTheme: {
        mode: {
          name: "dark",
          active: false,
        },
        theme: {
          name: "blue",
          active: true,
        },
      },

      activeIndex: 0,
    };
  },
  methods: {
    checkStorage(item, data) {
      if (localStorage.getItem(item) === null) {
        localStorage.setItem(item, JSON.stringify(data));
      }

      return localStorage.getItem(item);
    },

    setStorage(item, data) {
      localStorage.setItem(item, JSON.stringify(data));

      return localStorage.getItem(item);
    },

    changeTheme(obj) {
      console.table(obj);

      if (obj.mode === this.currentTheme.mode.name && obj.mode != undefined) {
        this.currentTheme.mode.active = !this.currentTheme.mode.active;
        this.currentTheme.mode.active
          ? (this.activeIndex = 1)
          : (this.activeIndex = 0);
        console.log(this.currentTheme.mode.active);
        console.log(this.activeIndex);
      }

      console.log(obj);
      console.log(!obj)
      if (obj.theme !== this.currentTheme.theme.name && obj.theme != undefined) {
        console.log(obj.theme)
        this.currentTheme.theme = {
          name: obj.theme,
          active: true
        }

        console.log(this.currentTheme.theme);
      }

      console.log(this.currentTheme)
      this.setStorage("theme", this.currentTheme);
      this.$emit("change-theme", {currentTheme: this.currentTheme, themes: this.themes.themes});
    },
  },
  mounted() {
    console.log(this.currentTheme);
    this.currentTheme = JSON.parse(
      this.checkStorage("theme", this.currentTheme)
    );
    console.log(this.currentTheme);

    this.currentTheme.mode.active = !this.currentTheme.mode.active;
    this.changeTheme({ mode: this.currentTheme.mode.name, theme: this.currentTheme.theme.name });
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/_utils.scss";

.theme-control {
  &__cont {
    position: fixed;
    top: $defValEm * 2;
    right: -2px;
    z-index: 7;
    min-width: $defValpx * 2.5;
    border-radius: $defValpx 0 0 $defValpx;

    &:hover,
    &:focus {
      & .themes {
        max-height: $defValpx * 8;
      }
    }
  }

  &__group {
    padding: 0 $defValpx / 2;
  }

  &__opt {
    border-radius: $defValpx / 2;
    margin: $defValpx / 2 0;
    width: $defValpx * 2.5;
    height: $defValpx * 2.5;
    // height: #{$defValpx * 2};
    cursor: pointer;
  }
}

.modes {
  // padding: 0 $defValpx / 2;

  &__mode {
    // border-radius: $defValpx / 2;
    // margin: $defValpx / 2 0;
    // width: $defValpx * 3;
    // height: $defValpx * 3;
    // // height: #{$defValpx * 2};
    // cursor: pointer;
    // text-align: center;

    display: flex;
    align-items: center;
    justify-content: center;
  }
}

.themes {
  overflow: hidden;
  max-height: 0px;
}
</style>