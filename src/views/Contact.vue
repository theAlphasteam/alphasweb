<template>
  <main class="">
    <section class="site-sect hero pad--t-7em">
      <div class="site-sect__wrapper max-width--1120">
        <div class="main-cont">
          <div class="form-cont glass glass--bg pad--2em m--2">
            <div class="form-cont__wrapper">
              <header class="form-cont__header">
                <div>
                  <h1 class="heading txt--h txt-4 bg--txt bg--txt-main-gradient heading">
                    Get in touch!
                  </h1>
                  <p>Contact us for a quote, help out to join the team</p>
                </div>

                <ul class="items my--2">
                  <li class="items__li cta cta--main-hover">
                    <div class="icon icon--md">
                      <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512">
                        <title>Location</title>
                        <circle cx="256" cy="192" r="32" />
                        <path
                          d="M256 32c-88.22 0-160 68.65-160 153 0 40.17 18.31 93.59 54.42 158.78 29 52.34 62.55 99.67 80 123.22a31.75 31.75 0 0051.22 0c17.42-23.55 51-70.88 80-123.22C397.69 278.61 416 225.19 416 185c0-84.35-71.78-153-160-153zm0 224a64 64 0 1164-64 64.07 64.07 0 01-64 64z" />
                      </svg>
                    </div>
                    <span>183 street kingsway</span>
                  </li>
                  <a href="tel:+2348135155549" class="items__li cta cta--main-hover">
                    <div class="icon icon--md">
                      <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512">
                        <title>Call</title>
                        <path
                          d="M391 480c-19.52 0-46.94-7.06-88-30-49.93-28-88.55-53.85-138.21-103.38C116.91 298.77 93.61 267.79 61 208.45c-36.84-67-30.56-102.12-23.54-117.13C45.82 73.38 58.16 62.65 74.11 52a176.3 176.3 0 0128.64-15.2c1-.43 1.93-.84 2.76-1.21 4.95-2.23 12.45-5.6 21.95-2 6.34 2.38 12 7.25 20.86 16 18.17 17.92 43 57.83 52.16 77.43 6.15 13.21 10.22 21.93 10.23 31.71 0 11.45-5.76 20.28-12.75 29.81-1.31 1.79-2.61 3.5-3.87 5.16-7.61 10-9.28 12.89-8.18 18.05 2.23 10.37 18.86 41.24 46.19 68.51s57.31 42.85 67.72 45.07c5.38 1.15 8.33-.59 18.65-8.47 1.48-1.13 3-2.3 4.59-3.47 10.66-7.93 19.08-13.54 30.26-13.54h.06c9.73 0 18.06 4.22 31.86 11.18 18 9.08 59.11 33.59 77.14 51.78 8.77 8.84 13.66 14.48 16.05 20.81 3.6 9.53.21 17-2 22-.37.83-.78 1.74-1.21 2.75a176.49 176.49 0 01-15.29 28.58c-10.63 15.9-21.4 28.21-39.38 36.58A67.42 67.42 0 01391 480z" />
                      </svg>
                    </div>
                    <span>+2348135155549</span>
                  </a>
                  <a href="mailto:miracleiodev@gmail.com" class="items__li cta cta--main-hover">
                    <div class="icon icon--md">
                      <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512">
                        <title>Mail</title>
                        <path
                          d="M424 80H88a56.06 56.06 0 00-56 56v240a56.06 56.06 0 0056 56h336a56.06 56.06 0 0056-56V136a56.06 56.06 0 00-56-56zm-14.18 92.63l-144 112a16 16 0 01-19.64 0l-144-112a16 16 0 1119.64-25.26L256 251.73l134.18-104.36a16 16 0 0119.64 25.26z" />
                      </svg>
                    </div>

                    <span>miracleiodev@gmail.com</span>
                  </a>
                </ul>
              </header>
              <div class="form glass glass--bg pad--2">
                <form name="main-form" id="main-form" action="https://formspree.io/f/xoqyanyy" method="POST"
                  data-netlify="true" @submit.prevent="processForm">
                  <!-- <input type="hidden" name="form-name" value="main-form" /> -->
                  <h1 class="mb--3 txt--h">Contact Form</h1>
                  <div class="form__wrapper grid grid--1-1">
                    <div class="form__inputs-cont">
                      <label class="form__input-label" for="name">Your Name</label>
                      <div tabindex="1" class="form__input-item">
                        <input id="name" name="name" type="text" placeholder="John Moe" required />
                      </div>
                      <label class="form__input-label" for="mail">Mail</label>
                      <div class="form__input-item">
                        <input id="mail" name="mail" type="email" placeholder="johnmoe@gmail.com" required />
                      </div>
                      <label class="form__input-label" for="phone">Phone</label>
                      <div class="form__input-item">
                        <input id="phone" type="text" placeholder="+234808080808" />
                      </div>
                    </div>
                    <div class="form__message-cont">
                      <label class="form__input-label" for="message">Message</label>
                      <textarea class="pad--2" name="message" id="message" cols="30" rows="10"
                        placeholder="Your message here" required></textarea>
                    </div>
                  </div>
                  <div class="form__wrapper mt--1">
                    <label class="form__input-label" for="">What services are you interested in?</label>
                    <div class="form__inputs-cont check-group">
                      <div class="form__input-item form__check-item">
                        <input type="checkbox" name="service" value="web-design" id="web-design" />
                        <label for="web-design" class="form__check-label">
                          <span> Web Design </span>
                        </label>
                      </div>
                      <div class="form__input-item form__check-item">
                        <input type="checkbox" name="service" value="web-dev" id="web-dev" />
                        <label for="web-dev" class="form__check-label">
                          <span> Web Developement </span>
                        </label>
                      </div>
                      <div class="form__input-item form__check-item">
                        <input type="checkbox" name="service" value="logo-design" id="logo-design" />
                        <label for="logo-design" class="form__check-label">
                          <span> Logo Design </span>
                        </label>
                      </div>
                    </div>
                  </div>
                  <div class="form__action-cont mt--2">
                    <button class="cta cta--main-gradient">Send a Message</button>
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- <div class="notif-bubble glass glass--bg">
      <h3>{{notifMessage.status}}</h3>
      <p>{{notifMessage.message}}</p>
    </div> -->

    <notif-bubble :bubbleData="notifMessage" ></notif-bubble>

  </main>
</template>

<script>
import NotifBubble from '../components/NotifBubble.vue';

  export default {

    data() {
      return {
        contactFormData: {},
        notifMessage: {
          status : "Ok",
          message : "Nothing here yet.."
        }
      };
    },

    components: {
      NotifBubble
    },

    methods: {
      submitForm(form, data) {
        fetch(form.action, {
            method: 'POST',
            headers: {
              // "Content-Type": "application/x-www-form-urlencoded",
              'Accept': 'application/json'
            },
            body: data
            // body: new URLSearchParams(this.contactFormData).toString()
          })
          .then((res) => {
            console.log("Form submitted");
            form.reset();
            console.log(res)

            this.notify(({
              status: res.ok ? "Ok" : res.status,
              message: `
              Thanks for filling the form, we'll get back to you as soon as possible.

              Stay Awesome! ✨✨
              `
              }))
            return res.json();
          })
          .then(data => {
            console.log(data)
          })
          .catch(err => {
            console.log(err);
            this.notify(({status: "Error", message: err}))
          })

      },
      processForm(e) {
        let form = e.target;
        console.log(e.target);
        this.contactFormData = new FormData(form);
        // let urlencodedForm = encodeURIComponent(this.contactFormData);
        console.log(this.contactFormData);

        this.submitForm(form, this.contactFormData)

      },
      notify(data){
        this.notifMessage = data;
      }
    },
  };
</script>

<style lang="scss" scoped>
  @import "../scss/_utils.scss";

  .about {
    background: var(--bg-2);

    &__hero {
      justify-content: center;
      text-align: center;

      &.hero__wrapper {
        width: 68%;
      }
    }
  }

  .main-cont {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .form-cont {
    height: 50%;
    width: 100%;
    border-radius: $defValpx * 1.5;
    // background: var(--main);
    // color: var(--txt);

    &__wrapper{

    }

    &__header {
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      text-align: center;
    }

    @media screen and (max-width: 767px){
        margin: 0;
        padding: 0;
        background: none;
        box-shadow: none;
        border-color: transparent;
    }

    @media screen and (min-width: 768px){
        &__wrapper{
          display: grid;
          grid-template-columns: 4fr 8fr;
          gap: $defValEm * 2;
        }

        &__header{
          justify-content: space-between;
          text-align: left;
        }
    }
  }

  .items {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    gap: $defValEm;
    flex-wrap: wrap;
    width: 100%;

    &__li {
      list-style-type: none;
      border-radius: $defValpx / 2;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: $defValEm / 2;
      border: 2px solid var(--main);
      flex-grow: 1;

      &:hover {
        // border-color: transparent;
      }

      // * {
      //   font-family: inherit;
      // }
    }

    @media screen and (min-width: 768px){
        &__li{
          justify-content: left;
        }
    }
  }

  .form {
    width: 100%;
    border-radius: $defValpx;

    &__input-label {
      display: block;
      margin-bottom: $defValpx;
      cursor: pointer;
    }

    &__wrapper {}

    &__inputs-cont {
      &.check-group {
        display: flex;
        gap: $defValpx;
        flex-direcetion: row;
        flex-wrap: wrap;
      }
    }

    &__input-item {
      width: 100%;
      padding: $defValpx;
      border-radius: $defValpx/2;
      background: var(--bg-2);
      border: 2px solid var(--dark-trans);
      margin-bottom: $defValpx * 1.5;

      input {
        width: 100%;
        border: none;
        outline: none;
        background: none;
      }
    }

    &__check-item {
      background: none;
      border: none;
      padding: 0;
      cursor: pointer;
      display: flex;
      flex-grow: 1;
      width: unset;
      margin: 0;

      input {
        position: absolute;
        opacity: 0;
        cursor: pointer;

        &:checked {
          &~label {
            border-color: var(--main);

            &,
            * {
              color: var(--main);
            }
          }
        }
      }
    }

    &__check-label {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      border: 2px solid transparent;
      border-radius: $defValpx / 2;
      padding: $defValpx;
      background: var(--bg-2);

      @include hover-scale();

      span {}
    }

    &__message-cont {
      textarea {
        width: 100%;
        border: none;
        outline: none;
        border-radius: $defValpx;
        resize: none;
        background: var(--bg-2);
      }
    }

    &__action-cont {
      display: flex;
      justify-content: center;
      align-items: center;
    }

    @media screen and (min-width: 768px){
      // background: var(--bg);
      box-shadow: none;
    }
  }

  .notif-bubble{
    position: fixed;
    bottom: 0;
    left: 50%;
    transform: translate(-50%, 100%);

    min-width: 120px;
    min-height: 40px;

    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding: 0.5em;
    gap: $defValEm;
    border-radius: $defValpx;

    &.active{
      transform: translate(-50%, -100%);
    }
  }
</style>