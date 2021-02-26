<template>
  <div class="theme-control__cont glass glass--bg">
    <div class="theme-control__modes">
      <ul class="modes">
        <li
          class="modes__mode"
          v-for="(mode, i) in themes.modes"
          v-bind:key="i"
          :title="mode.class"
          :style="{ 'background-color': mode.color }"
          @click="changeTheme({ mode: mode.class })"
        ></li>
      </ul>
    </div>
    <div class="theme-control__themes"></div>
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
            class: "dark",
            color: "var(--dark)",
          },
        ],
      },

      currentTheme: {
        mode: {
          name: "dark",
          active: false,
        },
      },
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
        if(obj.mode === this.currentTheme.mode.name){
            this.currentTheme.mode.active = !this.currentTheme.mode.active;
            console.log(this.currentTheme.mode.active)
        }

        this.setStorage("theme",this.currentTheme);
        this.$emit("change-theme", this.currentTheme)
    },
  },
  mounted() {
    this.currentTheme = JSON.parse(this.checkStorage("theme", this.currentTheme));
    this.currentTheme.mode.active = !this.currentTheme.mode.active;
    this.changeTheme({mode: this.currentTheme.mode.name});
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
    width: $defValEm * 2.5;
    border-radius: $defValpx 0 0 $defValpx;
  }
}

.modes {
  padding: 0 $defValpx / 2;

  &__mode {
    border-radius: $defValpx / 2;
    margin: $defValpx / 2 0;
    height: #{$defValpx * 1.5};
    cursor: pointer;
  }
}
</style>