<template>
  <site-header></site-header>
  <router-view class="pad--y-2em" />
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
@import '@/scss/main.scss';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  overflow-x: hidden;
  min-height: 100vh;

  *{
    transition: all 0.32s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  }
}
</style>
