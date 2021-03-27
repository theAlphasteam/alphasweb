<template>
  <header id="site-header" class="site-header">
    <div class="site-header__wrapper glass glass--bg max-width--1240">
      <figure class="site-logo" title="Alphasweb">
        <router-link to="/" class="site-logo__img-w-txt">
          <div class="site-logo__logo-cont">
            <svg xmlns="http://www.w3.org/2000/svg" class="site-logo__logo" viewBox="0 0 507 507" width="32" height="32">
              <title>alphasweb logo</title>
              <path
                d="M253.5,0h0C113.5,0,0,113.5,0,253.5H0C0,393.5,113.5,507,253.5,507h0C393.5,507,507,393.5,507,253.5h0C507,113.5,393.5,0,253.5,0ZM417.63,290.88A126.75,126.75,0,0,1,290.88,417.63h0A126.75,126.75,0,0,1,164.13,290.88h0A126.75,126.75,0,0,1,290.87,164.13h0A126.75,126.75,0,0,1,417.63,290.87Z"
              />
            </svg>
          </div>
          <h1 class="site-logo__logo-txt txt--h txt-1">alphasweb</h1>
        </router-link>
      </figure>
      <site-nav></site-nav>
    </div>
  </header>
</template>

<script>
import SiteNav from "./SiteNav.vue";

export default {
  name: "SiteHeader",
  components: {
    SiteNav,
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/_utils.scss";
@import "@/scss/_layout.scss";

.site-header {
  position: fixed;
  top: $defValEm * 2;
  width: 100%;
  z-index: 6;

  @supports(position: sticky){
    // position: sticky;
  }

  &__wrapper {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: $defValpx;
    // background: #fff;
    box-shadow: 12px 20px 72px var(--dark-trans);
    border-radius: $defValpx;
    width: calc(100% - #{$defValEm * 6});

    > * {
      display: inline-block;
      vertical-align: middle;
    }
  }
}

.site-logo {
  margin: 0;

  &__img-w-txt {
    > * {
      display: inline-block;
      vertical-align: middle;
      padding-right: $defValpx;
    }

    // display: flex;
    // justify-content: space-between;
    // align-items: center;
  }

  &__logo {
    width: 32px;
    height: 32px;

    *{
        fill: var(--main);
    }
  }

  &__logo-txt {
    // padding-left: $defValpx;
    color: var(--dark);
    // text-transform: capitalize;
    font-family: $header-font;
    letter-spacing: $defValpx / -12;
    font-weight: 900;
  }
}
</style>