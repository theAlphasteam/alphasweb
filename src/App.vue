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
}
</style>
