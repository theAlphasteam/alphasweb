<template>
  <section class="site-sect">
    <div class="site-sect__wrapper max-width--1120">
      <!-- <div class="bg bg--page">
        <div class="bg__img-cont overlay overlay--bg img-cont">
          <img src="@/assets/img/bg/a-pic-of-big-smallies.jpeg" alt="" />
        </div>
      </div> -->

      <header class="site-sect__header home__header pad--y-4em">
        <div class="grid grid--7-5">
          <div class="wrapper">
            <!-- <span class="heading">Hello,</span> -->
            <h1 class="heading heading--lg">
              We're the team in love with all things web and design.
            </h1>
            <p class="txt--p txt-1 mb--2">
              Lorem ipsum dolor sit amet consectetur, adipisicing elit. Sunt
              placeat, culpa facilis odio velit aperiam sapiente natus!
            </p>
            <router-link to="/about">
              <button class="cta cta--main">Get in touch</button>
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
  &__header {
    width: 100%;

    h1{
      line-height: $defValEm;
      color: var(--main);
      font-weight: 900;
    }
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


    &._2{
      top: 40%;
      left: 60%;
      width: 60%;
    }
  }
}
</style>
