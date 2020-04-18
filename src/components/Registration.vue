<template>
  <div class="registration">
    <!-- REGISTRATION -->
    <form class="registration-content">
      <div class="registration-content__gender">
        <span class="registration-content__description">Vaše pohlaví</span>
        <input id="registration-sex-man" class="hidden" name="sex" type="radio" value="man">
        <label for="registration-sex-man" class="registration-content__sex">
          <i class="fas fa-mars"></i>
        </label>
        <input id="registration-sex-woman" class="hidden" name="sex" type="radio" value="woman">
        <label for="registration-sex-woman" class="registration-content__sex">
          <i class="fas fa-venus"></i>
        </label>
      </div>
      <input class="registration-content__input" type="text" placeholder="Uživatelské jméno">
      <select class="registration-content__select">
        <option value="">Věk</option>
        <option value="18">18 let</option>
        <option value="19">19 let</option>
        <option value="20">20 let</option>
      </select>
      <input class="registration-content__input" type="text" placeholder="Město">
      <input class="registration-content__input" type="password" placeholder="Vaše heslo">
      <input class="registration-content__input" type="password" placeholder="Znovu heslo">
      <button
        type="button"
        class="btn btn--primary btn--radius btn--shadow btn--big"
        @click="goNextFN('Profil', selectedComponents)"
      >Chci se registrovat</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Registration",
  props: {
    selectedComponents: String,
    goNextFN: Function
  },
  data() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_registration.scss";
</style>


