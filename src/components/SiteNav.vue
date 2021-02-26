<template>
  <nav id="site-nav">
    <router-link to="/about">
      <button class="cta cta--main-gradient">Contact Us</button>
    </router-link>
  </nav>
</template>

<script>
export default {
    name: "SiteNav"
};
</script>

<style lang="scss" scoped>
    @import '@/scss/_utils.scss';
</style>