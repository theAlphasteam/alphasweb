<template>
  <header id="site-header" class="site-header">
      <div class="site-header__wrapper glass glass--bg max-width--1240">
        <figure class="site-logo" title="Alphasweb">
            <router-link to="/" class="site-logo__img-w-txt">
                <!-- <div class="site-logo__logo-cont">
                    <img src="../assets/batman.png" alt="Alphasweb Logo" title="Alphasweb logo" class="site-logo__logo">
                </div> -->
                <h1 class="site-logo__logo-txt">webalphas</h1>
            </router-link>
        </figure>
        <site-nav></site-nav>
      </div>
  </header>
</template>

<script>
import SiteNav from './SiteNav.vue'


export default {
    name: 'SiteHeader',
    components: {
        SiteNav
    }
}
</script>

<style lang="scss" scoped>
    @import '@/scss/_utils.scss';
    @import '@/scss/_layout.scss';

    .site-header{
        position: fixed;
        top: $defValEm * 2;
        width: 100%;
        z-index: 3;

        &__wrapper{
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: $defValpx;
            // background: #fff;
            box-shadow: 12px 20px 72px rgba(0, 0, 0, 0.08);
            border-radius: 0 0 $defValpx $defValpx;
            border-radius: $defValpx;
            width: calc(100% - #{$defValEm * 2});

            > *{
                display: inline-block;
                vertical-align: middle;
            }
        }

    }

    .site-logo{
        margin: 0;

        &__img-w-txt{
            > *{
                display: inline-block;
                vertical-align: middle;
                padding-right: $defValpx;
            }

            // display: flex;
            // justify-content: space-between;
            // align-items: center;
        }

        &__logo{
            width: 32px;
        }

        &__logo-txt{
            padding-left: $defValpx;
            color: var(--dark);
            // text-transform: capitalize;
            font-family: $header-font;
            font-size: x-large;
            letter-spacing: $defValpx / -12;
            font-weight: 900;
        }
    }
</style>