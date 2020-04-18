<template>
  <div class="home">
    <!-- INTRO -->
    <div class="logo">
      <img class="logo__img" src="~/public/images/girl-white.png">
      <h1 class="logo__title1">FREE</h1>
      <h2 class="logo__title2">CHAT</h2>
    </div>

    <p class="home__stats">{{getRandomUsers}} dívek online</p>

    <!-- TASKS --
    <button
      type="button"
      class="home__component-button btn btn--primary btn--radius"
      @click="showPopUpFN(datas.popUp1.profileImg, 
      datas.popUp1.title, 
      datas.popUp1.doubleRowTitle, 
      datas.popUp1.message, 
      datas.popUp1.btnHorizontal,
      datas.popUp1.btn1Text, 
      datas.popUp1.btn1Class, 
      datas.popUp1.btn2Text, 
      datas.popUp1.btn2Class)"
    >Show popup #1</button>
    
    <button
      type="button"
      class="home__component-button btn btn--primary btn--radius"
      @click="showPopUpFN(datas.popUp2.profileImg, 
      datas.popUp2.title, 
      datas.popUp2.doubleRowTitle, 
      datas.popUp2.message, 
      datas.popUp2.btnHorizontal,
      datas.popUp2.btn1Text, 
      datas.popUp2.btn1Class, 
      datas.popUp2.btn2Text, 
      datas.popUp2.btn2Class)"
    >Show popup #2</button>-->
    <button
      type="button"
      class="home__button btn btn--primary btn--dark btn--radius btn--shadow btn--big"
      @click="goNextFN('Process', selectedComponent)"
    >Registrovat se</button>
    
    <button
      type="button"
      class="home__button btn btn--primary btn--dark btn--radius btn--shadow btn--big"
      @click="goNextFN('Login', selectedComponent)"
    >Přihlásit se</button>

    <!-- CONTACT --
    <a
      href="tel:777556047"
      class="home__contact-button btn btn--primary btn--radius btn--border"
    >Zavolat řešiteli</a>-->
  </div>
</template>

<script>
export default {
  name: "Home",
  props: {
    selectedComponent: String,
    goNextFN: Function
  },
  data() {
    return {
      minUsersOnline: 50,
      maxUsersOnline: 300,
      datas: {
        popUp1: {
          profileImg: "",
          title: "Milý uživateli",
          doubleRowTitle: true,
          message: "Prosím, aktualizujte si váš profil.",
          btnHorizontal: false,
          btn1Text: "Aktualizovat",
          btn1Class: "btn btn--primary btn--radius btn--shadow",
          btn2Text: "Zavřít",
          btn2Class: "btn"
        },
        popUp2: {
          profileImg: "../images/girl.png",
          title: "Perfektní!",
          doubleRowTitle: false,
          message: "Váš profil byl aktualizován.",
          btnHorizontal: true,
          btn1Text: "Nastavení",
          btn1Class: "btn btn--border btn--radius",
          btn2Text: "Pokračovat",
          btn2Class: "btn btn--primary btn--radius"
        }
      }
    };
  },
  computed: {
    getRandomUsers() {
      return Math.floor(Math.random() * this.maxUsersOnline) + this.minUsersOnline;
    }
  }
};
</script>

<style lang="scss">
@import "../assets/scss/_home.scss";
</style>