<template>
  <div class="wrapper wrapper--themes">
    <div class="slide slide--title">
      <transition name="fade">
        <h1 v-if="show == 0 || show == 1">Les Règles</h1>
      </transition>
      <transition name="fade">
        <div class="scroll" v-if="show == 0">scroll vers le bas <img src="../assets/img/down.gif"></div>
      </transition>
      <transition name="fade">
        <h2 v-if="show == 1">
          Une société déshumanisante poussant au nihilisme
        </h2>
      </transition>
    </div>
    <div class="slide slide--intro" v-if="show == 2">
      <div class="intro__background"></div>
      <div class="intro__content">
        <div class="intro__title subtitle">
          La société de consommation
        </div>
        <div class="intro__details details">
          Notre société est complètement monopolisée par la culture de la
          consommation et l'obsession des possessions.
        </div>
      </div>
    </div>
    <transition name="fade">
      <div
        class="slide slide--bar"
        v-if="show == 3"
        :class="{firstPlan: show ==3}"
      >
        <video
          class="bar__video"
          src="../assets/vids/bar.mp4"
          autoplay
          ref="barVideo"
          @ended="increment"
        ></video>
        <div class="sound__wrapper" v-if="show == 3">
          video
          <button
            class="sound sound--true"
            v-if="show == 3 && audioVideoFirst == true"
            v-on:click="muteFirst"
          ></button>
          <button
            class="sound sound--false"
            v-if="show == 3 && audioVideoFirst == false"
            v-on:click="muteFirst"
          ></button>
        </div>
        <button class="play-pause" v-if="show == 3" v-on:click="playFirst"></button>
      </div>
    </transition>
    <div class="slide slide--consommations">
      <transition name="fade">
        <div class="consommation__title subtitle" v-if="show == 4">
          La société de consommation
        </div>
      </transition>
      <div class="consommation__content details">
        <transition name="backgroundConso">
          <div class="consommation__content--background" v-if="show == 4"></div>
        </transition>
        <transition name="fade">
          <div class="consommation__content--wrapper" v-if="show == 4">
            <div class="content__wrapper--text">
              <div>
                Le narrateur n’est personne, il n’a pas de passion autre que sa
                consommation.
              </div>
              <div class="wrapper__bold">Il vit sans but.</div>
              <div>
                Il est tellement absorbé par la possession d’objets qu’il se
                définit par ses possessions matérielles :
              </div>
            </div>
            <img
              src="../assets/img/consommation-scriptFirst.png"
              alt="image du script"
            />
          </div>
        </transition>
      </div>
      <transition name="fade">
        <img
          src="../assets/img/consommation-book.png"
          alt="image du livre"
          class="consommation__book"
          v-if="show == 4"
        />
      </transition>
    </div>
    <transition name="fade">
      <div
        class="slide slide--things"
        :class="{firstPlan: show == 5}"
        v-if="show == 5"
      >
        <div class="things__title subtitle">La société de consommation</div>
        <div class="things__wrapper">
          <div class="things__illustration">
            <img
              src="../assets/img/things.png"
              alt="illustration"
              class="things__illustration--image"
            />
            <img
              src="../assets/img/things-script.png"
              alt="script"
              class="things__illustration--script"
            />
          </div>
          <div class="things__content">
            <div class="content__quote">
              « Il m'a fallu une vie entière pour acheter tous ces trucs. »
            </div>
            <div class="content__details details">
              <div>
                L’importance et le sens de sa vie est mesurée par les objets
                qu’il possède. Décrivant sa propre existence à rien de plus
                qu’une façon de garder et de ranger des choses.
              </div>
              <div>
                Le consumérisme vide et sinistre incriminé dans Fight Club
                illustre également la solitude latente du narrateur.
              </div>
            </div>
          </div>
        </div>
        <img
          src="../assets/img/funfact.png"
          alt="funfact"
          class="things__funfact"
        />
        <div class="things__book">
          <div class="things__book--content">
            <div class="things__book--text">
              La structure laquée d'entretien facile de mes tables d'appoint
              Kalix.
              <br />
              Mes tables-gigognes Steg. <br />
              On achète des meubles. On se dit : ce sera le dernier canapé dont
              j'aurai jamais besoin de toute mon existence. On achète le canapé,
              et pendant quelques années on se satisfait du fait que, quoi qui
              puisse arriver, au moins on a réglé le problème du canapé. Et
              ensuite le bon service de table. Ensuite le lit parfait. Les
              rideaux. Le tapis.
            </div>
          </div>
        </div>
      </div>
    </transition>
    <transition name="fade">
      <div class="slide slide--nihilisme" v-if="show == 6">
        <div class="nihilisme__title subtitle">
          Le nihilisme
        </div>
        <div class="nihilisme__details--wrapper">
          <div class="nihilisme__details details">
            Le nihilisme soutient que la vie n’a pas de sens, rejette toutes
            valeurs, croyances ou réalités substantielles.
          </div>
          <div class="nihilisme__details details">
            C'est un rejet total de la vie.
          </div>
        </div>
        <div class="nihilisme__bobine--wrapper">
          <div class="nihilisme__bobine"></div>
        </div>
        <div class="nihilisme__details details">
          Un monde dans lequel nous n’avons pas de morale, pas d’objets, pas de
          pensées idéologiques, rien du tout.
        </div>
      </div>
    </transition>
    <transition name="fade">
      <div class="slide slide--soap" v-if="show == 7">
        <video
          class="soap__video"
          src="../assets/vids/soap.mp4"
          autoplay
          ref="soapVideo"
          @ended="increment"
        ></video>
        <div class="sound__wrapper" v-if="show == 7">
          video
          <button
            class="sound sound--true"
            v-if="show == 7 && audioVideoSecond == true"
            v-on:click="muteSecond"
          ></button>
          <button
            class="sound sound--false"
            v-if="show == 7 && audioVideoSecond == false"
            v-on:click="muteSecond"
          ></button>
        </div>
        <button class="play-pause" v-if="show == 7" v-on:click="playSecond"></button>
      </div>
    </transition>
    <transition name="fade">
      <div
        class="slide slide--papers"
        :class="{firstPlan: show == 8}"
        v-if="show == 8"
      >
        <div class="papers__title subtitle">Le nihilisme</div>
        <div class="papers__wrapper">
          <img
            v-on:click="papers"
            class="papers__paper0 papers"
            src="../assets/img/papers-paper0.png"
            alt="passage du livre"
          />
          <img
            class="papers__paper1 papers"
            src="../assets/img/papers-paper1.png"
            alt="analyse"
          />
          <img
            class="papers__paper2 papers"
            src="../assets/img/papers-paper2.png"
            alt="analyse"
          />
          <img
            class="papers__paper3 papers"
            src="../assets/img/papers-paper3.png"
            alt="analyse"
          />
          <img
            class="papers__polaroid0 papers"
            src="../assets/img/papers-polaroid0.png"
            alt="polaroid"
          />
          <img
            class="papers__polaroid1 papers"
            src="../assets/img/papers-polaroid1.png"
            alt="polaroid"
          />
          <img
            class="papers__polaroid2 papers"
            src="../assets/img/papers-polaroid2.png"
            alt="polaroid"
          />
        </div>
      </div>
    </transition>
    <transition name="fade">
      <div class="slide slide--autodestruction" v-if="show == 9">
        <div class="autodestruction__background">
          <div class="autodestruction__wrapper">
            <div class="autodestruction__title subtitle">
              L'autodestruction
            </div>
            <div class="autodestruction__content">
              <div class="autodestruction__content--quote">
                « Tyler dit que chercher à s'améliorer, c'est rien que de la
                branlette. Tyler dit que l'autodestruction est sans doute la
                réponse. »
              </div>
              <div class="autodestruction__content--details details">
                Se détruire pour se reconstruire. Le narrateur réalise qu’il
                peut s’évader de son existence et creuser une vision bien plus
                excitante et profonde de la vie humaine.
              </div>
            </div>
          </div>
        </div>
      </div>
    </transition>
    <transition name="fade">
      <div class="slide slide--conclusionSecond" v-if="show == 10">
        <video
          class="conclusionSecond__video"
          src="../assets/vids/bobine.mp4"
          autoplay
          ref="bobineVideo"
          @ended="afterEnd"
        ></video>
        <div class="sound__wrapper" v-if="show == 10">
          video
          <button
            class="sound sound--true"
            v-if="show == 10 && audioVideoThird == true"
            v-on:click="muteThird"
          ></button>
          <button
            class="sound sound--false"
            v-if="show == 10 && audioVideoThird == false"
            v-on:click="muteThird"
          ></button>
        </div>
        <button class="play-pause" v-if="show == 10" v-on:click="playThird"></button>
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
        if (this.$refs.barVideo.muted) {
          this.$refs.barVideo.muted = false;
          this.audioVideoFirst = true;
        } else {
          this.$refs.barVideo.muted = true;
          this.audioVideoFirst = false;
        }
      },

      playFirst: function() {
        if (this.$refs.barVideo.paused) {
          this.$refs.barVideo.play();
        } else {
          this.$refs.barVideo.pause();
        }
      },

      muteSecond: function() {
        if (this.$refs.soapVideo.muted) {
          this.$refs.soapVideo.muted = false;
          this.audioVideoSecond = true;
        } else {
          this.$refs.soapVideo.muted = true;
          this.audioVideoSecond = false;
        }
      },

      playSecond: function() {
        if (this.$refs.soapVideo.paused) {
          this.$refs.soapVideo.play();
        } else {
          this.$refs.soapVideo.pause();
        }
      },

      muteThird: function() {
        if (this.$refs.bobineVideo.muted) {
          this.$refs.bobineVideo.muted = false;
          this.audioVideoThird = true;
        } else {
          this.$refs.bobineVideo.muted = true;
          this.audioVideoThird = false;
        }
      },

      playThird: function() {
        if (this.$refs.bobineVideo.paused) {
          this.$refs.bobineVideo.play();
        } else {
          this.$refs.bobineVideo.pause();
        }
      },

      play: function() {
        console.log(this.$refs.conclusionVideo.paused);
        if (this.$refs.conclusionVideo.paused) {
          this.$refs.conclusionVideo.play();
        } else {
          this.$refs.conclusionVideo.pause();
        }
      },

      afterEnd: function() {
        this.$router.push({ path: "../Chaos" });
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

  .intro__background {
    background-image: url("../assets/img/consommation-background.png");
    height: 100vh;
    width: 100vw;
    background-size: cover;
    background-repeat: no-repeat;
    z-index: -1;
  }

  .intro__content {
    position: absolute;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .intro__details {
    margin-top: 15px;
  }

  .bar__video {
    height: 100vh;
    width: 100vw;
  }

  .consommation__title {
    position: absolute;
    text-align: center;
    margin: 0 auto;
    left: 0;
    right: 0;
    top: 10vh;
  }

  .consommation__content {
    display: flex;
    flex-direction: row;
    width: 90vw;
    height: 100vh;
    align-items: flex-end;
  }

  .consommation__content--background {
    width: 45vw;
    height: 85vh;
    background-image: url("../assets/img/bar-background.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    transform: translateY(11vh);
  }

  .consommation__content--wrapper {
    margin-left: 50px;
    height: 50vh;
    width: 380px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    transform: translateY(-7vh);
  }

  .content__wrapper--text {
    height: 50%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .wrapper__bold {
    font-weight: bold;
  }

  .consommation__book {
    position: absolute;
    width: auto;
    height: 70vh;
    right: -300px;
    bottom: 0;
    transition: transform 0.3s;
  }

  .consommation__book:hover {
    transform: translateX(-300px);
  }

  .slide--things {
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
  }

  .things__wrapper {
    height: 70vh;
    width: 80vw;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
  }

  .things__illustration {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .things__illustration--script {
    width: 421px;
    height: 198px;
  }

  .things__content {
    width: 402px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 390px;
    transform: translateY(80px);
  }

  .content__quote {
    font-size: 26px;
    font-weight: bold;
    line-height: 110%;
  }

  .content__details {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 225px;
  }

  .things__funfact,
  .things__book {
    position: absolute;
  }

  .things__funfact {
    right: -360px;
    height: 300px;
    bottom: 70px;
    transition: all 0.5s;
    z-index: 2;
  }

  .things__funfact:hover {
    transform: rotate(90deg) translateY(285px) translateX(-50px);
  }

  .things__book {
    width: 527px;
    height: 160px;
    overflow: hidden;
    background-image: url("../assets/img/things-paper.png");
    background-size: contain;
    background-repeat: no-repeat;
    right: -470px;
    bottom: 450px;
    transition: all 0.3s;
  }

  .things__book:hover {
    transform: translateX(-470px);
  }

  .things__book--content {
    color: #222222;
    font-family: "Times New Roman", Times, serif;
    font-size: 17px;
    line-height: 180%;
    left: 60px;
    top: 20px;
    width: 500px;
    position: relative;
    transition: all 7s linear;
  }

  .things__book--content:hover {
    transform: translateY(-150px);
  }

  .things__book--text {
    width: 430px;
  }

  .slide--nihilisme {
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
  }

  .nihilisme__bobine--wrapper {
    width: 100vw;
    overflow: hidden;
  }

  .nihilisme__bobine {
    background-image: url("../assets/img/nihilisme-bobine.png");
    width: 2732px;
    height: 261px;
    background-repeat: no-repeat;
    background-position: right;
    animation: bobine 15s linear infinite;
  }

  .nihilisme__details--wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100px;
  }

  .nihilisme__details {
    width: 592px;
  }

  .soap__video {
    width: 100vw;
    height: 100vh;
  }

  .slide--papers {
    display: flex;
    align-items: center;
  }

  .papers__title {
    position: absolute;
    top: 7vh;
    margin: 0 auto;
    right: 0;
    left: 0;
    text-align: center;
  }

  .papers__wrapper {
    position: absolute;
    margin: 0 auto;
    right: 0;
    left: 0;
    height: 480px;
    width: 400px;
    transform: translateY(40px);
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .papers {
    position: absolute;
    transition: all 0.3s;
  }

  .papers__paper0 {
    z-index: 3;
  }

  .papers__paper1 {
    z-index: 2;
  }

  .papers__wrapper:hover .papers__paper1 {
    transform: translateX(-400px) translateY(-100px) rotate(-2deg);
  }

  .papers__paper2 {
    z-index: 1;
  }

  .papers__wrapper:hover .papers__paper2 {
    transform: translateX(-360px) translateY(130px);
  }

  .papers__paper3 {
    z-index: 2;
  }

  .papers__wrapper:hover .papers__paper3 {
    transform: translateX(340px) translateY(130px);
  }

  .papers__polaroid0 {
    z-index: 0;
  }

  .papers__wrapper:hover .papers__polaroid0 {
    transform: translateX(-160px) translateY(-85px);
  }

  .papers__polaroid1 {
    z-index: 1;
  }

  .papers__wrapper:hover .papers__polaroid1 {
    transform: translateX(160px) translateY(-60px);
  }

  .papers__polaroid2 {
    z-index: 0;
  }

  .papers__wrapper:hover .papers__polaroid2 {
    transform: translateX(330px) translateY(-100px);
  }

  .slide--autodestruction {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .autodestruction__background {
    width: 1166px;
    height: 522px;
    background-image: url("../assets/img/autodestruction-bp.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    transition: all 0.3s;
  }

  .autodestruction__background:hover {
    background-image: url("../assets/img/autodestruction-en.jpg");
  }

  .autodestruction__wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 55%;
    width: 625px;
    margin: 0 0 40px 40px;
  }

  .autodestruction__content--quote {
    font-size: 25px;
    font-weight: normal;
    line-height: 120%;
  }

  .autodestruction__content {
    height: 190px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .conclusionSecond__video {
    width: 100vw;
    height: 100vh;
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

  .backgroundConso-enter-active,
  .backgroundConso-leave-active {
    transition: all 0.5s;
  }

  .backgroundConso-enter {
    width: 100vw;
    height: 100vh;
    transform: none;
  }

  .backgroundConso-leave-to {
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
</style>
