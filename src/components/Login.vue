<template>
  <div class="login">
    <!-- REGISTRATION -->
    <form class="login-content">
      <p class="login-content__title">Seznamte se s novými přáteli</p>
      <input class="login-content__input" type="text" placeholder="Uživatelské jméno">
      <input class="login-content__input" type="password" placeholder="Heslo">
      <button @click="goNextFN('Profil', selectedComponent)" type="button" class="btn btn--primary btn--radius btn--shadow btn--big">Přihlásit se</button>
      <p class="login-content__description">Nemáte ještě účet?
        <a href="#" class="login-content__link">Zaregistrujte ještě dnes!</a>
      </p>
    </form>
  </div>
</template>

<script>
export default {
  name: "Login",
  props: {
    selectedComponent: String,
    goNextFN: Function
  },
  data() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/pages/_login.scss";
</style>


