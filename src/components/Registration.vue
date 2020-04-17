<template>
  <div class="registration">
    <!-- TITLE -->
    <h2 class="registration__title">Jak to funguje?</h2>

    <!-- STEP -->
    <div class="registration__steps">
      <div class="step" v-for="(item, x) in steps" :key="x">
        <img class="step__img" :src="item.stepImg">
        <div class="step__box">
          <h2 class="step__title">{{item.stepTitle}}</h2>
          <a class="step__link" v-if="item.stepLink" href="#">{{item.stepDescription}}</a>
          <span class="step__text" v-if="!item.stepLink">{{item.stepDescription}}</span>
        </div>
      </div>
    </div>

    <!-- BACK HOME -->
    <button
      type="button"
      class="registration__back btn btn--primary btn--radius btn--shadow btn--big"
      @click="showPageFN('Login')"
    >Chci účet</button>
  </div>
</template>

<script>
export default {
  name: "Registration",
  props: {
    selectedComponent: String,
    showPageFN: Function
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
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_registration.scss";
</style>


