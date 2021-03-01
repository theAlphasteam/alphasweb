<template>
  <section class="about hero site-sect pad--y-7em">
    <div class="site-sect__wrapper max-width--1120">
      <div class="main-cont">
        <div class="form-cont">
          <header class="form-cont__header">
            <h1 class="txt--h txt-4 heading">Get in touch!</h1>
            <p>Contact us for a quote, help out to join the team</p>
            <ul class="items my--2">
              <li class="items__li cta cta--main-hover">183 street kingsway</li>
              <li class="items__li cta cta--main-hover">+234808080808</li>
              <li class="items__li cta cta--main-hover">miracleio@gmail.com</li>
            </ul>
          </header>
          <div class="form glass glass--bg pad--2">
            <form>
              <h1 class="mb--3 txt--h">Contact Form</h1>
              <div class="form__wrapper grid grid--1-1">
                <div class="form__inputs-cont">
                  <label for="name">Your Name</label>
                  <div class="form__input-item">
                    <input id="name" type="text" placeholder="John Moe" />
                  </div>
                  <label for="Mail">Mail</label>
                  <div class="form__input-item">
                    <input id="Mail" type="email" placeholder="johnmoe@gmail.com" />
                  </div>
                  <label for="Phone">Phone</label>
                  <div class="form__input-item">
                    <input id="Phone" type="text" placeholder="+234808080808" />
                  </div>
                </div>
                <div class="form__message-cont">
                  <label for="Message">Message</label>
                  <textarea
                    class="pad--2"
                    name=""
                    id="Message"
                    cols="30"
                    rows="10"
                    placeholder="Your message here"
                  ></textarea>
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
  </section>
</template>



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

.site-sect {
  position: relative;
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

  &__header {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
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

  &__li {
    list-style-type: none;
    border-radius: $defValpx / 2;
  }
}

.form {
  width: 100%;
  border-radius: $defValpx;

  label {
    display: block;
    margin-bottom: $defValpx/1.5;
  }

  &__wrapper {
  }

  &__input-item {
    width: 100%;
    padding: $defValpx;
    border-radius: $defValpx/2;
    // background: var(--bg);
    border: 2px solid var(--dark-trans-blur);
    margin-bottom: $defValpx * 1.5;

    input {
      width: 100%;
      border: none;
      outline: none;
      background: none;
    }
  }

  &__message-cont {
    textarea {
      width: 100%;
      border: none;
      outline: none;
      border-radius: $defValpx;
      resize: none;
      background: var(--bg);
    }
  }
  &__action-cont{
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>
