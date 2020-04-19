<template>
  <div class="home">
    <!-- INTRO -->
    <transition enter-to-class="animated zoomIn" appear>
      <div class="logo">
        <img class="logo__img" src="~/public/images/girl-white.png">
        <h1 class="logo__title1">FREE</h1>
        <h2 class="logo__title2">CHAT</h2>
      </div>
    </transition>

    <!-- ONLINE USERS -->
    <transition enter-to-class="animated pulse delay-1s" appear>
      <p class="home__stats">{{getRandomUsers}} dívek online</p>
    </transition>

    <!-- BUTTONS -->
    <transition enter-to-class="animated fadeInUp fast" appear>
      <button
        type="button"
        class="home__button btn btn--primary btn--dark btn--radius btn--shadow btn--big"
        @click="goNextFN('Process', selectedComponent)"
      >Registrovat se</button>
    </transition>
    <transition enter-to-class="animated fadeInUp fast" appear>
      <button
        type="button"
        class="home__button btn btn--primary btn--dark btn--radius btn--shadow btn--big"
        @click="goNextFN('Login', selectedComponent)"
      >Přihlásit se</button>
    </transition>

    <!-- DARK MODE -->
    <div class="switcher">
      <span class="switcher__description">dark mode</span>
      <input
        v-model="onDarkMode"
        @input="updateDarkMode"
        @change="updateDarkMode"
        id="switcher-dark"
        class="hidden"
        name="darkmode"
        type="checkbox"
        value="dark"
      >
      <label for="switcher-dark" class="switcher__toggle">
        <i v-if="onDarkMode" class="fas fa-toggle-on"></i>
        <i v-if="!onDarkMode" class="fas fa-toggle-off"></i>
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  props: {
    selectedComponent: String,
    onDarkMode: Boolean,
    goNextFN: Function
  },
  data() {
    return {
      minUsersOnline: 50,
      maxUsersOnline: 300
    };
  },
  methods: {
    updateDarkMode() {
      this.$emit("update-dark-mode", this.onDarkMode);
    }
  },
  computed: {
    getRandomUsers() {
      return (
        Math.floor(Math.random() * this.maxUsersOnline) + this.minUsersOnline
      );
    }
  }
};
</script>

<style lang="scss">
@import "../assets/scss/pages/_home.scss";
</style>