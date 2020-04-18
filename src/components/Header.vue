<template>
  <header class="header">
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
    <h1
      v-bind:class="{'header__title--without-l-icon' : (selectedComponent == ''), 'header__title--without-r-icon' : (selectedComponent == 'Process' || selectedComponent == 'Registration' || selectedComponent == 'Login')}"
      class="header__title"
    >{{pageTitle(selectedComponent)}}</h1>
    <button
      v-if="selectedComponent == 'Profil'"
      type="button"
      class="btn btn--icon btn--invert"
      @click="goNextFN('Home', selectedComponent)"
    >
      <i class="fas fa-sign-out-alt"></i>
    </button>
  </header>
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
      if (page === "Process") {
        return "Registrace";
      } else if (page === "Registration") {
        return "Vytvoření účtu";
      } else if (page === "Login") {
        return "Přihlásit se";
      } else if (page === "Profil") {
        return "Váš profil";
      }
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_header.scss";
</style>

