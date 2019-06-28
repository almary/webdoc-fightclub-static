E<template>
  <div class="wrapper wrapper--themes">
    <div class="slide slide--title">
      <transition name="fade">
        <h1 v-if="show == 0 || show == 1">Le Chaos</h1>
      </transition>
      <transition name="fade">
        <div class="scroll" v-if="show == 0">
          scroll vers le bas <img src="../assets/img/down.gif" />
        </div>
      </transition>
      <transition name="fade">
        <h2 v-if="show == 1">
          Le besoin de s’échapper par le chaos pour se sentir vivre
        </h2>
      </transition>
    </div>
    <transition name="fade">
      <div
        class="slide slide--intro"
        v-if="show == 2"
        :class="{firstPlan: show == 2}"
      >
        <video
          class="intro__video"
          src="../assets/vids/giveup.mp4"
          autoplay
          ref="introVideo"
          @ended="increment"
        ></video>
        <div class="sound__wrapper" v-if="show == 2">
          video
          <button
            class="sound sound--true"
            v-if="show == 2 && audioVideoFirst == true"
            v-on:click="muteFirst"
          ></button>
          <button
            class="sound sound--false"
            v-if="show == 2 && audioVideoFirst == false"
            v-on:click="muteFirst"
          ></button>
        </div>
        <button
          class="play-pause"
          v-if="show == 2"
          v-on:click="playFirst"
        ></button>
      </div>
    </transition>
    <transition name="fade">
      <div class="slide slide--rupture" v-if="show == 3">
        <div class="rupture__title subtitle">Rupture sociale</div>
        <div class="rupture__wrapper">
          <div class="rupture__content details">
            <div>
              Seule la désolation de la solitude et l'abscence totale de tout ce
              qui rendrait le narrateur vivant pourrait prédisposer un homme à
              désirer l'excitation et l'acceptation sociale nonobstant des
              conséquences à long terme.
            </div>
            <div>
              Comme décrit dans le film, la solitude s'accompagne d'une
              réinvention incessante de soi-même, une transformation d'une
              existence morne à excitante, de morale à immorale, de mauviette à
              "vrai homme".
            </div>
          </div>
          <div class="rupture__polaroid">
            <img
              class="rupture__polaroid--1"
              src="../assets/img/rupture-1.png"
              alt="polaroid"
            />
            <img
              class="rupture__polaroid--2"
              src="../assets/img/rupture-2.png"
              alt="polaroid"
            />
          </div>
        </div>
      </div>
    </transition>
    <transition name="fade">
      <div
        class="slide slide--vivre"
        v-if="show == 4"
        :class="{firstPlan: show == 4}"
      >
        <div class="vivre__title subtitle">Se sentir vivre</div>
        <img
          class="vivre__script"
          src="../assets/img/vivre-script.png"
          alt="script"
        />
      </div>
    </transition>
    <transition name="fade">
      <div
        class="slide slide--crash"
        v-if="show == 5"
        :class="{firstPlan: show ==5}"
      >
        <video
          class="crash__video"
          src="../assets/vids/crash.mp4"
          autoplay
          @ended="increment"
          ref="crashVideo"
        ></video>
        <div class="sound__wrapper" v-if="show == 5">
          video
          <button
            class="sound sound--true"
            v-if="show == 5 && audioVideoSecond == true"
            v-on:click="muteSecond"
          ></button>
          <button
            class="sound sound--false"
            v-if="show == 5 && audioVideoSecond == false"
            v-on:click="muteSecond"
          ></button>
        </div>
        <button
          class="play-pause"
          v-if="show == 5"
          v-on:click="playSecond"
        ></button>
      </div>
    </transition>
    <transition name="fade">
      <div
        class="slide slide--mort"
        v-if="show == 6"
        :class="{firstPlan: show == 6}"
      >
        <div class="mort__title subtitle">
          Le rapport à la mort
        </div>
        <div class="mort__polaroid">
          <img
            class="mort__polaroid--1"
            src="../assets/img/mort-polaroid.png"
            alt="polaroid"
          />
          <img
            class="mort__polaroid--2"
            src="../assets/img/mort-polaroid-back.png"
            alt="dos polaroid"
          />
        </div>
        <div class="mort__content">
          <div class="mort__content--details">
            « Méditer la mort, c’est méditer la liberté ; celui qui sait mourir,
            ne sait plus être esclave »<span class="details">, Sénèque</span>
          </div>
          <img
            class="mort__content--book"
            src="../assets/img/mort-book.png"
            alt="passage du livre"
          />
        </div>
      </div>
    </transition>
    <transition name="fade">
      <div class="slide slide--recul" v-if="show == 7">
        <div class="recul__content ">
          <div class="recul__title subtitle">Prise de recul</div>
          <div class="recul__details details">
            <div>
              C’est à la mort de Bob, que Jack prend conscience qu’il doit
              empêcher Tyler d’aller plus loin. Bob a été utilisé pour le
              projet, comme un moyen.
            </div>
            <div class="recul__content--wrapper">
              <div>
                Se rebeller contre un système qui les abruti ne leur permet pas
                de se libérer; cela les déshumanise.
              </div>
              <div>
                Ce projet finit par déshumaniser les hommes, au lieu de les
                grandir, il nie les individus au profit d’une cause commune.
              </div>
            </div>
          </div>
        </div>
        <img
          class="recul__background"
          src="../assets/img/recul.jpg"
          alt="images du film"
        />
      </div>
    </transition>
    <div class="slide slide--end">
      <div class="end__wrapper">
        <transition name="fade">
          <img
            src="../assets/img/end-background.jpg"
            class="end__background"
            v-if="show == 8"
          />
        </transition>
        <div class="end__details details">
          <transition name="appears">
            <span class="end__details--1" v-if="show == 8">
              À la fin, les buildings tombent,</span
            >
          </transition>
          <transition name="appears2">
            <span class="end__details--2" v-if="show == 8"
              >les matériaux n’existent plus,</span
            >
          </transition>
          <transition name="appears3">
            <span class="end__details--3" v-if="show == 8">
              tout est calme.</span
            >
          </transition>
        </div>
      </div>
    </div>
    <transition name="fade">
      <div
        class="slide slide--conclusion"
        v-if="show == 9"
        :class="{firstPlan: show == 9}"
      >
        <video
          class="conclusion__video"
          src="../assets/vids/conclusion.mp4"
          autoplay
          ref="conclusionVideo"
          @ended="increment"
        ></video>
        <div class="sound__wrapper" v-if="show == 9">
          video
          <button
            class="sound sound--true"
            v-if="show == 9 && audioVideoThird == true"
            v-on:click="muteThird"
          ></button>
          <button
            class="sound sound--false"
            v-if="show == 9 && audioVideoThird == false"
            v-on:click="muteThird"
          ></button>
        </div>
        <button
          class="play-pause"
          v-if="show == 9"
          v-on:click="playThird"
        ></button>
      </div>
    </transition>
    <transition name="fade">
      <div class="slide slide--final" v-if="show == 10">
        <div class="final__wrapper">
          <div class="final__title subtitle">
            Merci d'avoir parcouru ce documentaire.
          </div>
          <router-link to="/"><button>Recommencer</button> </router-link>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
  export default {
    props: ["show"],

    data() {
      return {
        audioVideoFirst: true,
        audioVideoSecond: true,
        audioVideoThird: true
      };
    },

    methods: {
      increment: function() {
        this.$emit("increment");
      },

      muteFirst: function() {
        if (this.$refs.introVideo.muted) {
          this.$refs.introVideo.muted = false;
          this.audioVideoFirst = true;
        } else {
          this.$refs.introVideo.muted = true;
          this.audioVideoFirst = false;
        }
      },

      playFirst: function() {
        if (this.$refs.introVideo.paused) {
          this.$refs.introVideo.play();
        } else {
          this.$refs.introVideo.pause();
        }
      },

      muteSecond: function() {
        if (this.$refs.crashVideo.muted) {
          this.$refs.crashVideo.muted = false;
          this.audioVideoSecond = true;
        } else {
          this.$refs.crashVideo.muted = true;
          this.audioVideoSecond = false;
        }
      },

      playSecond: function() {
        if (this.$refs.crashVideo.paused) {
          this.$refs.crashVideo.play();
        } else {
          this.$refs.crashVideo.pause();
        }
      },

      muteThird: function() {
        if (this.$refs.conclusionVideo.muted) {
          this.$refs.conclusionVideo.muted = false;
          this.audioVideoThird = true;
        } else {
          this.$refs.conclusionVideo.muted = true;
          this.audioVideoThird = false;
        }
      },

      playThird: function() {
        console.log(this.$refs.conclusionVideo.paused);
        if (this.$refs.conclusionVideo.paused) {
          this.$refs.conclusionVideo.play();
        } else {
          this.$refs.conclusionVideo.pause();
        }
      }
    }
  };
</script>

<style scoped>
  .noBackground {
    background: none;
  }

  h2 {
    position: absolute;
    transform: translateY(50px);
  }

  .firstPlan {
    z-index: 1;
  }

  .subtitle {
    font-family: "Univers Next Pro Ext", "sans-serif";
    font-weight: bold;
    font-size: 44px;
  }

  .details {
    font-size: 22px;
    font-weight: 100;
    line-height: 120%;
  }

  .slide--title {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .intro__video {
    width: 100vw;
    height: 100vh;
  }

  .slide--rupture {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .rupture__title {
    position: absolute;
    top: 7vh;
  }

  .rupture__wrapper {
    width: 80vw;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
  }

  .rupture__content {
    width: 530px;
    display: flex;
    flex-direction: column;
    height: 260px;
    justify-content: space-between;
  }

  .rupture__polaroid {
    width: 30vw;
  }

  .rupture__polaroid--1,
  .rupture__polaroid--2 {
    height: auto;
    width: 30vw;
  }

  .rupture__polaroid--1 {
    animation: polaroid 7s infinite alternate ease-in-out;
  }

  .rupture__polaroid--2 {
    animation: polaroid 7s infinite alternate-reverse ease-in-out;
  }

  .slide--vivre {
    background-image: url("../assets/img/vivre-background.jpg");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .vivre__script {
    position: absolute;
    bottom: -250px;
    transition: all 0.3s;
  }

  .vivre__script:hover {
    transform: translateY(-250px);
  }

  .crash__video {
    width: 100vw;
    height: 100vh;
  }

  .slide--mort {
    margin: 0 auto;
    right: 0;
    left: 0;
    display: flex;
    flex-direction: row;
    width: 90vw;
    justify-content: space-around;
    align-items: center;
  }

  .mort__title {
    position: absolute;
    top: 7vh;
  }

  .mort__polaroid {
    position: relative;
    width: 532px;
    height: 514px;
    transform-style: preserve-3d;
  }

  .mort__polaroid:hover .mort__polaroid--1 {
    transform: rotateY(180deg);
  }

  .mort__polaroid:hover .mort__polaroid--2 {
    transform: rotateY(360deg);
  }

  .mort__polaroid--1,
  .mort__polaroid--2 {
    position: absolute;
    transition: all 0.5s;
  }

  .mort__polaroid--1 {
    z-index: 1;
  }

  .mort__polaroid--2 {
    transform: rotateY(180deg);
  }

  .mort__content {
    height: 480px;
    width: 592px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    transform: translateY(40px);
  }

  .mort__content--details {
    font-size: 27px;
    font-weight: bold;
  }

  .slide--recul {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
  }

  .recul__content {
    width: 466px;
    height: 450px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .recul__details {
    height: 350px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .recul__content--wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 170px;
  }

  .slide--end {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .end__wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
  }

  .end__background {
    width: 1052px;
    height: 420px;
    position: absolute;
  }

  .end__details {
    width: 303px;
    text-align: center;
    position: absolute;
  }

  /* .end__details--1 {
    opacity: 0;
    transition: all 0.5s;
  }
  .end__details--2 {
    opacity: 0;
    transition: all 0.5s;
  }
  .end__details--3 {
    opacity: 1;
    transition: all 0.5s;
  } */

  .conclusion__video {
    width: 100vw;
    height: 100vh;
  }

  .slide--final {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .final__wrapper {
    height: 300px;
    width: 800px;
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
  }

  /* ANIMS SCOPED */

  .text-enter-active,
  .text-leave-active {
    transition: all 0.5s;
  }
  .text-enter,
  .text-leave-to {
    opacity: 0;
    transform: translateY(20px);
  }

  .appears-enter-active {
    transition: all 0.5s;
    transition-delay: 0s;
  }
  .appears-enter {
    opacity: 0;
  }
  .appears-leave-active {
    transition: all 0.5s;
  }
  .appears-leave-to {
    opacity: 0;
  }

  .appears2-enter-active {
    transition: all 0.5s;
    transition-delay: 1s;
  }
  .appears2-enter {
    opacity: 0;
  }
  .appears2-leave-active {
    transition: all 0.5s;
  }
  .appears2-leave-to {
    opacity: 0;
  }

  .appears3-enter-active {
    transition: all 0.5s;
    transition-delay: 2s;
  }
  .appears3-enter {
    opacity: 0;
  }
  .appears3-leave-active {
    transition: all 0.5s;
  }
  .appears3-leave-to {
    opacity: 0;
  }

  .bobine-enter-active {
    transition: all 1s;
  }
  .bobine-leave-active {
    transition: all 1s;
  }
  .bobine-enter {
    transform: translateY(200vh);
  }
  .bobine-leave-to {
    transform: translateY(-200vh);
  }

  @keyframes bobine {
    0% {
      transform: none;
    }

    97% {
      transform: translate(-700px);
    }

    100% {
      transform: none;
    }
  }

  @keyframes polaroid {
    0% {
      transform: none;
    }

    100% {
      transform: translateY(-20px);
    }
  }
</style>
