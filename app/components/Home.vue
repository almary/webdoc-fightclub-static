<template>
  <div class="wrapper">
    <div class="mobile" v-if="mobile == 1">
      <div class="mobile__title">Fight Club</div>
      <div class="mobile__description">
        Ce site est optimisé pour une navigation sur ordinateur, pour le
        découvrir veuillez changer d'appareil.
      </div>
    </div>
    <div class="video">
      <transition name="fade">
        <video
          v-if="show == 1"
          src="../assets/vids/intro.mp4"
          autoplay
          ref="introVid"
          @ended="afterEnd"
        ></video>
      </transition>
        <transition name="fade">
          <div class="skip__wrapper" v-if="show == 1">
            passer
        <button class="skip"  v-on:click="afterEnd">
          </div>
        </button>
      </transition>
      <transition name="fade">
        <div class="sound__wrapper" v-if="show == 1">
          video
          <button
            class="sound sound--true"
            v-if="show == 1 && audioVideo == true"
            v-on:click="unmute"
          ></button>
          <button
            class="sound sound--false"
            v-if="show == 1 && audioVideo == false"
            v-on:click="unmute"
          ></button>
        </div>
      </transition>
    </div>
    <transition name="fade">
      <div class="content" v-if="show == 0">
        <div>
          <transition name="fade">
            <h1 v-if="show == 0" class="title">Fight Club</h1>
          </transition>
          <transition name="fade">
            <h2 v-if="show == 0">
              Comment un environnement monotone modèle-t-il une pensée poussant au
              chaos ?
            </h2>
          </transition>
        </div>
        <transition name="fade">
          <button class="commencer" v-if="show == 0" v-on:click="increment">
            Commencer
          </button>
        </transition>
      </div>
    </transition>
    <div class="disclaimer">Ce site à été réalisé à des fins pédagogiques dans le cadre du cursus Bachelor de l’école HETIC. Les contenus présentés ne sont en aucun cas exploités à des fins commerciales et ne seront pas publiés.</div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        audioVideo: true,
        mobile: 0,
        show: 0
      };
    },

    methods: {
      increment: function() {
        this.show++;
      },

      afterEnd: function() {
        this.$router.push({ path: "Homme" });
      },

      unmute: function() {
        if (this.$refs.introVid.muted) {
          this.$refs.introVid.muted = false;
          this.audioVideo = true;
        } else {
          this.$refs.introVid.muted = true;
          this.audioVideo = false;
        }
      },

      start: function() {
        if (navigator.userAgent.toLowerCase().indexOf("firefox") === -1) {
          window.removeEventListener("wheel", this.scroll, { passive: true });
        } else {
          window.removeEventListener("DOMMouseScroll", this.scrollFirefox, {
            passive: true
          });
        }
        this.$router.push({ path: "Homme" });
      },

      mobileFunction: function() {
        console.log("resize");
        if (window.innerWidth < 1100 || window.innerHeight < 600) {
          this.mobile = 1;
        } else {
          this.mobile = 0;
        }
      }
    },

    created() {
      this.mobileFunction();
      window.addEventListener("resize", this.mobileFunction);
    },
    destroyed() {
      window.removeEventListener("resize", this.mobileFunction);
    }
  };
</script>

<style scoped>
  video {
    height: 100vh;
  }

  .wrapper {
    width: 100vw;
    height: 100vh;
    background-color: black;
    background-image: url("../assets/img/scratch.png");
    background-repeat: no-repeat;
    background-size: cover;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .content {
    background-color: black;
    background-image: url("../assets/img/home-background.png");
    background-size: cover;
    background-repeat: no-repeat;
    height: 100vh;
    width: 100vw;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    text-align: center;
  }

  .h2 {
    position: relative;
  }

  .title {
    font-size: 200px;
    height: 200px;
  }

  .commencer {
    position: absolute;
    bottom: 50px;
    padding: 15px 30px;
    background-color: rgba(159, 34, 29, 0.5);
  }
  .commencer:hover {
    background-color: rgba(159, 34, 29, 1);
  }

  
  .disclaimer {
    position: absolute;
    text-align: center;
    margin: 0 auto;
    left: 0;
    right: 0;
    bottom: 0px;
    color: #acacac;
    font-size: 12px;
  }
</style>
