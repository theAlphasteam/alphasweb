<template>
  <section class="site-sect">
    <div class="site-sect__wrapper max-width--1120">
      <!-- <div class="bg bg--page">
        <div class="bg__img-cont overlay overlay--bg img-cont">
          <img src="@/assets/img/bg/a-pic-of-big-smallies.jpeg" alt="" />
        </div>
      </div> -->

      <header class="site-sect__header home__hero hero pad--y-6em">
        <div class="grid grid--7-5">
          <div class="wrapper">
            <!-- <span class="heading">Hello,</span> -->
            <h1 class="heading heading--lg hero__caption bg--txt bg--txt-main-gradient">
              We're the team in love with all things web and design.
            </h1>
            <p class="txt--p txt-1 mb--2">
              Our job is to bring out the best part of the web for you, us and everyone else!
            </p>
            <router-link to="/about">
              <button class="cta cta--main-gradient">Get in touch</button>
            </router-link>
          </div>
          <div class="hero-media">
            <div class="hero-media__img img-cont _1">
              <img src="../assets/img/1024-editor.png" alt="A peeling orange" title="Code editor">
            </div>
            <div class="hero-media__img img-cont _2">
              <img src="../assets/batman.png" alt="The batman" title="The batman">
            </div>
          </div>
        </div>
      </header>
    </div>

    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  </section>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    // HelloWorld,
  },
};
</script>

<style lang="scss" scoped>
  @import '../scss/_utils.scss';

.home {
  &__hero {

  }
}

.hero-media{
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  &__img{
    position: absolute;
    top: - $defValEm;
    left: 0;
    animation: float 5s ease-in-out alternate-reverse infinite;

    @for $var from 0 to 3 {
      &:nth-child(#{$var}){
        animation-duration: 5s + $var / 2;
      }
    }

    &._2{
      top: 40%;
      left: 60%;
      width: 60%;
    }
  }
}

@keyframes float {
  0%{
    transform: translateY(0);
  }

  50%{
    transform: translateY(10%);
  }

  100%{
    transform: translateY(-10%);
  }
}
</style>
