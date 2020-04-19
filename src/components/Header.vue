<template>
  <div class="header">
    <!-- LEFT ICON -->
    <button
      v-if="selectedComponent != 'Profil'"
      @click="goBackFN"
      type="button"
      class="btn btn--icon btn--invert"
    >
      <i class="fas fa-chevron-left"></i>
    </button>
    <button
      v-if="selectedComponent == 'Profil'"
      @click="goNextFN('Home', selectedComponent)"
      type="button"
      class="btn btn--icon btn--invert"
    >
      <i class="fas fa-bars"></i>
    </button>

    <!-- TITLE -->
    <h1
      v-bind:class="{'header__title--without-l-icon' : (selectedComponent == ''), 'header__title--without-r-icon' : (selectedComponent == 'Process' || selectedComponent == 'Registration' || selectedComponent == 'Login')}"
      class="header__title"
    >{{pageTitle(selectedComponent)}}</h1>

    <!-- RIGHT ICON -->
    <button
      v-if="selectedComponent == 'Profil'"
      @click="goNextFN('Home', selectedComponent)"
      type="button"
      class="btn btn--icon btn--invert"
    >
      <i class="fas fa-sign-out-alt"></i>
    </button>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    selectedComponent: String,
    goBackFN: Function,
    goNextFN: Function
  },
  methods: {
    pageTitle(page) {
      switch (page) {
        case "Process":
          return "Registrace";
        case "Registration":
          return "Vytvoření účtu";
        case "Login":
          return "Přihlásit se";
        case "Profil":
          return "Váš profil";
        default:
          return "FREE CHAT";
      }
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/modules/_header.scss";
</style>

