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
          <template v-for="project in projects" :key="project.id">
            <project-card @hook:mounted="alert('mounted')" :project="project" :isLoaded="projectLoaded"
              :id="project.id" />
          </template>
        </div>
      </div>
    </section>
    <notif-bubble :bubbleData="notifMessage"></notif-bubble>
  </main>
</template>

<script>
  import {
    defineAsyncComponent
  } from 'vue';
  import NotifBubble from '../components/NotifBubble.vue';
  // import ProjectCard from '../components/ProjectCard.vue';
  // @ is an alias to /src
  // import HelloWorld from "@/components/HelloWorld.vue";

  export default {
    name: "Home",
    components: {
      // dynamic import ?
      ProjectCard: defineAsyncComponent(() => import('../components/ProjectCard.vue')),
      NotifBubble
      // HelloWorld,
    },
    data() {
      return {
        projectLoaded: false,
        storedData: "",
        notifMessage: {
          status: "Ok",
          message: "Nothing here yet..",
        },
        projects: [{
            id: 1,
            name: 'alphasweb',
            link: 'https://alphasweb.netlify.app',
            data_url: "https://api.github.com/repos/thealphasteam/alphasweb",
            description: 'alphasweb official portfolio site',
            collaborators: [{
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
            ],
            fetched_data: {}
          },
          {
            id: 2,
            name: 'Oshare',
            link: 'https://alphasweb.netlify.app',
            data_url: "https://api.github.com/repos/miracleonyenma/oshare",
            description: 'Simple file sharing app built with VueJS',
            collaborators: [{
                id: 1,
                username: 'miracleio'
              },
              {
                id: 2,
                username: 'miracleio'
              },
              {
                id: 3,
                username: 'miracleio'
              },
              {
                id: 4,
                username: 'miracleio'
              },
            ],
            technologies: [
              'vue', 'scss'
            ],
            fetched_data: {}
          }
        ],
        projectsStatus: [{
          id: 326528589,
          updated: false,
          local: false
        }]
      }
    },
    methods: {
      // try to fetch project data from
      // localstorage and API
      // #1 set project data to locasStorage data:
      //  if API data is not available (No internet)
      // #2 set project data and localStorage data to API data:
      //  if API is available

      async fetchData() {
        let isUpdated = false; // before fetch data is not updated
        let isStored = false; // set to false before attempting to get localStorage data

        // clear contents of projectsStatus
        this.projectsStatus = []

        // try fetching local data from localStorage
        let localProjectsData = this.getData('projects');
        if(localProjectsData){ //if localStorage is not null || undefined || "" i.e contains data 🚧 still needs validation!! 🚧
          isStored = true; // data has been stored previously
          this.projects = localProjectsData // #1 set all projects data to localStorage data
        }

        // console.log('isStored: ', isStored);

        try {
          // map projects data to Promise in order to run async functions and resolve at once
          await Promise.all(
            this.projects.map(async (project) => {
              let newID; //new ID
              let randomID = Math.floor(Math.random(999) * 1000000); //random integer
              try {
                // if project.url contains data
                if (project.data_url) {
                  let response = await fetch(project.data_url); //fetch API data
                  let data = await response.json() //get json

                  // #2 set project data to API data
                  project.fetched_data = data; // put API data in fetched_data field in individual project data

                  newID = data.id; // set newID to ID to API id
                  project.id = newID; // set project ID to newID id

                  // console.log(data);
                } else { // if project url contains no data
                  newID = randomID; // set newID to randomID
                  project.id = newID; // set project ID to newID
                }

                // update projectsStatus with newID, status(update status i.e if updatedfrom API), local
                // local is false because data is from API not localStorage
                this.populateStatus(newID, true, false);

                isUpdated = true; // data has been updated from API

              } catch (error) { // if fetch fails (INTERNET ERROR)

                console.log('Caught: ', error);

                // if data is not in localStorage or project fetched data is empty 🚧 requires more validation 🚧
                if(!isStored || project.fetched_data === {}){
                  console.log(`isStored: ${isStored}, project.fetched_data: ${JSON.stringify(project.fetched_data)}`)

                  newID = randomID; // set newID to random integer
                  project.id = newID; // set project ID to newID

                // update projectsStatus with newID, status(update status i.e if updatedfrom API), local
                // status is false because data has not been updated from API
                // local is false because data is not from localStorage
                  this.populateStatus(newID, false, false);

                } else{ // if data is in localStorage && has fetched data

                  newID = project.fetched_data.id; // set newID to fetched_data.id

                // update projectsStatus with newID, status(update status i.e if updatedfrom API), local
                // status is false because data has not been updated from API
                // local is true because data is from localStorage not API
                  this.populateStatus(newID, false, true); //

                }

                // console.log(project)

                throw error; // throw error to be caught by parent try catch block notify the error
              }
            }))

          this.projectLoaded = true; // projects can be loaded since data has been obtained either from API or localStorage

        } catch (error) { // catch error from Promise.all

          console.log('All caught up: ', error);

          // run notifyBubble
          this.notify({
            status: "ERROR",
            message: `Oops... we weren't able to update some project data`
          });

          isUpdated = false; // data has not been updated from API
        }

        return isUpdated
        // let newID;
        // fetch(project.data_url)
        //   .then(res => res.json())
        //   .then(data => {
        //     project.fetched_data = data
        //     newID = data.id;
        //     project.id = newID
        //   })
        //   .catch(err => {
        //     console.log(err)
        //     this.notify({
        //       status: "ERROR",
        //       message: "Oops... we weren't able to update some project data"
        //     });
        //     project.id = Math.floor(Math.random(999) * 1000000);
        //   });




      },
      // function to populate projectStatus with stats
      populateStatus(id, status, local) {

        // console.log(id, status, local);

        try { // check if such obj exists and update

          // generate projectStatus data with arguments
          let statusObj = {
            id: id,
            status: status,
            local: local
          };

          // get Index of in projectsStatus by ID
          // to see if such project status exists already
          let statusObjIndex = this.projectsStatus.findIndex(statusObj => {
            return statusObj.id === id
          });


          // console.log(statusObjIndex);

          if (statusObjIndex == -1) { // if no data exists on projectsStatus array:

            this.projectsStatus.push(statusObj); // push generated data to array

            statusObjIndex = this.projectsStatus.indexOf(statusObj) // get index of newly pushed data

            // console.log(`pushed at ${statusObjIndex}`, this.projectsStatus[statusObjIndex].id);

          } else { // if data with argument ID exists already:

            this.projectsStatus[statusObjIndex] = statusObj; // replace with generated data

            // console.log("updated: ", this.projectsStatus[statusObjIndex].id);
          }

          // console.log(statusObjIndex, this.projectsStatus[statusObjIndex]);

        } catch (error) { // catch error
          console.log('populate error: ', error)
        }
      },
      saveData(data) {
        localStorage.setItem("projectData", JSON.stringify(data))
      },
      getData(name) {
        return this.parseJSON(localStorage.getItem(name))
      },
      notify(data) {
        this.notifMessage = data
      },
      parseJSON(json) {
        try {
          return JSON.parse(json);
        } catch (error) {
          console.error("Handled: ", error)
          return json
        }
      }
    },
    watch: {
      projects: {
        deep: true,

        handler() {
          this.projectLoaded = true
        }
      },
      projectsStatus: {
        deep: true,

        handler() {
          localStorage.setItem('projectsStatus', JSON.stringify(this.projectsStatus));
        }
      }
    },
    mounted() {
      this.fetchData().then(() => {
        console.log(this.projects)
        localStorage.setItem('projects', JSON.stringify(this.projects))
        console.log(this.parseJSON(localStorage.getItem('projects')))
      })

    },
    beforeMount() {

    }
  };
</script>

<style lang="scss" scoped>
  @import '../scss/_utils.scss';

  .home {
    &__hero {}
  }

  .hero-media {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 280px;
    width: 100%;

    &__img {
      position: absolute;
      top: - $defValEm * 4;
      left: 0;
      animation: float 5s ease-in-out alternate-reverse infinite;

      @for $var from 0 to 3 {
        &:nth-child(#{$var}) {
          animation-duration: 5s + $var / 2;
        }
      }

      &._2 {
        top: 28%;
        left: 60%;
        width: 60%;
      }
    }
  }

  @keyframes float {
    0% {
      transform: translateY(0);
    }

    50% {
      transform: translateY(10%);
    }

    100% {
      transform: translateY(-10%);
    }
  }

  .projects {
    &__header {
      // text-align: right;
    }

    &__gallery {
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: $defValEm * 2;
    }
  }
</style>