<template>
  <div class="process">
    <!-- TITLE -->
    <h2 class="process__title">Jak to funguje?</h2>

    <!-- STEP -->
    <div class="process__steps">
      <div class="step" v-for="(item, x) in steps" :key="x">
        <img class="step__img" :src="item.stepImg">
        <div class="step__box">
          <h2 class="step__title">{{item.stepTitle}}</h2>
          <a class="step__link" v-if="item.stepLink" href="#">{{item.stepDescription}}</a>
          <span class="step__text" v-if="!item.stepLink">{{item.stepDescription}}</span>
        </div>
      </div>
    </div>

    <!-- GO REGISTRATION -->
    <button
      type="button"
      class="process__continue btn btn--primary btn--radius btn--shadow btn--big"
      @click="goNextFN('Registration', selectedComponent)"
    >Chci účet</button>
  </div>
</template>

<script>
export default {
  name: "Process",
  props: {
    selectedComponent: String,
    goNextFN: Function
  },
  data() {
    return {
      steps: [
        {
          stepImg: "../images/step1.png",
          stepTitle: "Create account",
          stepDescription:
            "Signing up is easy, it will take just a minute and then you are ready to receive gifts",
          stepLink: true
        },
        {
          stepImg: "../images/step2.png",
          stepTitle: "Share your life",
          stepDescription:
            "Set prices and start chat with people, post pictures & videos, make calls. Everything you",
          stepLink: false
        },
        {
          stepImg: "../images/step2.png",
          stepTitle: "Earn money",
          stepDescription:
            "Earn bonus and monthly rewards for your photos and videos",
          stepLink: false
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/pages/_process.scss";
</style>


