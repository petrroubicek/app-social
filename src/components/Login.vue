<template>
  <div class="login">
    <!-- REGISTRATION -->
    <div class="login-content">
      <p class="login-content__description"></p>
      <input class="login-content__input" type="text" placeholder="Uživatelské jméno">
      <input class="login-content__input" type="password" placeholder="Heslo">
      <p class="login-content__description">
        Nemáte ještě účet?
        <a href="#" class="login-content__link">Zaregistrujte ještě dnes!</a>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  props: {
    showHomeFN: Function
  },
  data() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_login.scss";
</style>


