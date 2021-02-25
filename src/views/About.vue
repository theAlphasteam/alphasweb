<template>
  <section class="about hero">
    <div class="bg bg--page">
      <div class="bg__img-cont overlay overlay--dark img-cont">
        <img src="@/assets/img/bg/a-pic-of-big-smallies.jpeg" alt="">
      </div>
    </div>
    <header class="about__hero hero">
      <div class="hero__wrapper">
        <h1 class="bg--txt bg--txt-bg hero__caption txt--h txt-5">We can't wait to get in touch</h1>
      </div>
    </header>
  </section>
</template>

<style lang="scss" scoped>
  @import '../scss/_utils.scss';

  .about{
    &__hero{
      justify-content: center;
      text-align: center;

      &.hero__wrapper{
        width: 68%;
      }
    }

  }
</style>