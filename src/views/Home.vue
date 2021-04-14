<template>
  <main class="">
    <section class="site-sect">
      <div class="site-sect__wrapper max-width--1120">
        <!-- <div class="bg bg--page">
          <div class="bg__img-cont overlay overlay--bg img-cont">
            <img src="@/assets/img/bg/a-pic-of-big-smallies.jpeg" alt="" />
          </div>
        </div> -->

        <header class="site-sect__header home__hero hero pad--y-8em">
          <div class="grid grid--7-5">
            <div data-wa-trans="wrapper" class="wrapper">
              <!-- <span class="heading">Hello,</span> -->
              <h1 data-wa-trans="child" class="heading heading--lg hero__caption bg--txt bg--txt-main-gradient">
                We're the team in love with all things web and design.
              </h1>
              <p data-wa-trans="child" class="txt--p txt-1 mb--2">
                Our job is to bring out the best part of the web for you, us and everyone else!
              </p>
              <div data-wa-trans="child" class="action-cont">
                <router-link to="/contact">
                  <button class="cta cta--main-gradient">Get in touch</button>
                </router-link>
              </div>
            </div>
            <div data-wa-trans="child" class="hero-media grid__first max-width--420">
              <div class="hero-media__img img-cont _1">
                <img src="../assets/img/1024-editor.png" alt="A peeling orange" title="Code editor">
              </div>
              <div class="hero-media__img img-cont _2">
                <img src="../assets/img/batman.png" alt="The batman" title="The batman">
              </div>
            </div>
          </div>
        </header>
      </div>
    </section>

    <section class="projects site-sect pad--b-2em">
      <div class="site-sect__wrapper max-width--1120">
        <header class="projects__header mb--4">
          <h1 class="heading txt txt--h txt-4">Projects</h1>
          <p class="txt--p txt-1">
            Here's what we've been up to
          </p>
        </header>
        <div class="projects__gallery grid">
          <article v-for="project in projects" :key="project.id" class="projects__item project glass glass--bg pad--2">
            <header>
              <h3 class="txt--h txt-1">
                <a :href="project.link" v-if="project.link" target="_blank" rel="noopener noreferrer">
                  <span>{{project.name}}</span>

                  <span class="icon icon--sm">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="-3 -3 24 24" width="24" height="24" preserveAspectRatio="xMinYMin" class="jam jam-link"><path d='M3.19 9.345a.97.97 0 0 1 1.37 0 .966.966 0 0 1 0 1.367l-2.055 2.052a1.932 1.932 0 0 0 0 2.735 1.94 1.94 0 0 0 2.74 0l4.794-4.787a.966.966 0 0 0 0-1.367.966.966 0 0 1 0-1.368.97.97 0 0 1 1.37 0 2.898 2.898 0 0 1 0 4.103l-4.795 4.787a3.879 3.879 0 0 1-5.48 0 3.864 3.864 0 0 1 0-5.47L3.19 9.344zm11.62-.69a.97.97 0 0 1-1.37 0 .966.966 0 0 1 0-1.367l2.055-2.052a1.932 1.932 0 0 0 0-2.735 1.94 1.94 0 0 0-2.74 0L7.962 7.288a.966.966 0 0 0 0 1.367.966.966 0 0 1 0 1.368.97.97 0 0 1-1.37 0 2.898 2.898 0 0 1 0-4.103l4.795-4.787a3.879 3.879 0 0 1 5.48 0 3.864 3.864 0 0 1 0 5.47L14.81 8.656z'/></svg>
                  </span>
                </a>
                <span v-else>{{project.name}}</span>
              </h3>
              <p class="txt--p">{{project.description}}</p>

              <div class="project__stats mt--1">
                <span>{{project.collaborators.length}} collaborators</span>
              </div>
            </header>

            <div class="project__action-cont">
              <ul class="project__members">
                <template v-for="(member, index) in project.collaborators" :key="member.id">
                  <li class="project__member" v-if="index <= 1" v-bind:title="member.name">

                  </li>
                </template>

                <span v-if="project.collaborators.length - 2 > 0">+{{project.collaborators.length - 2}} more</span>
              </ul>

              <button class="cta cta--main-gradient">View more</button>
            </div>
          </article>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    // HelloWorld,
  },
  data(){
    return{
      projects: [
        {
          id: 1,
          name: 'alphasweb',
          link: 'http://alphasweb.netlify.app',
          description: 'alphasweb official portfolio site',
          collaborators: [
            {
              id: 1,
              username: 'miracleio'
            },
            {
              id: 2,
              username: 'shori'
            },
            {
              id: 3,
              username: 'Divo'
            }
          ],
          technologies: [
            'vue', 'scss'
          ]
        },
        {
          id: 2,
          name: 'Oshare',
          description: 'Simple file sharing app built with VueJS',
          collaborators: [
            {
              id: 1,
              username: 'miracleio'
            }
          ],
          technologies: [
            'vue', 'scss'
          ]
        }
      ]
    }
  }
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
  min-height: 280px;
  width: 100%;

  &__img{
    position: absolute;
    top: - $defValEm * 4;
    left: 0;
    animation: float 5s ease-in-out alternate-reverse infinite;

    @for $var from 0 to 3 {
      &:nth-child(#{$var}){
        animation-duration: 5s + $var / 2;
      }
    }

    &._2{
      top: 28%;
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

.projects{
  &__header{
    // text-align: right;
  }
  &__gallery{
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: $defValEm * 2;
  }
}

.project{
  width: 100%;
  min-height: 200px;
  border-radius: $defValpx;

  display: flex;
  flex-direction: column;
  justify-content: space-between;

  &__stats{
    opacity: .4;
  }

  &__action-cont{
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &__members{
    display: inline-flex;
    align-items: center;

    :nth-child(1){
      left: 0;
    }
  }

  &__member{
    position: relative;
    width: 28px;
    height: 28px;
    border-radius: 50%;
    background: var(--main-gradient);
    border: 1px solid var(--dark);

    left: - $defValpx;
  }
}

</style>
