<template>
  <div
    id="app"
    v-bind:class="{'body--bg-purple' : (currentPage == 'Home'), 'body--bg-gray' : (currentPage != 'Home')}"
  >
    <!-- HEADER -->
    <Header
      v-if="currentPage != 'Home'"
      :selectedComponent="currentPage"
      :selectedPage="pageName"
      :pastComponent="lastPage"
    ></Header>

    <!-- CONTENT -->
    <div class="container">
      <!-- HOMEPAGE -->
      <Home
        v-if="currentPage == 'Home'"
        :selectedComponent="currentPage"
        :showPageFN="showPage"
        :showPopUpFN="showPopUp"
      ></Home>

      <!-- POPUP -->
      <PopUp
        v-if="currentPage == 'PopUp'"
        :selectedComponent="currentPage"
        :profileImg="popUp.profileImg"
        :title="popUp.title"
        :doubleRowTitle="popUp.doubleRowTitle"
        :message="popUp.message"
        :btnHorizontal="popUp.btnHorizontal"
        :btn1Text="popUp.btn1Text"
        :btn1Class="popUp.btn1Class"
        :btn2Text="popUp.btn2Text"
        :btn2Class="popUp.btn2Class"
        :showPageFN="showPage"
        :showPopUpFN="showPopUp"
      ></PopUp>

      <!-- REGISTRATION -->
      <Registration
        v-if="currentPage == 'Registration'"
        :selectedComponent="currentPage"
        :selectedPage="pageName"
        :showPageFN="showPage"
      ></Registration>

      <!-- LOGIN -->
      <Login
        v-if="currentPage == 'Login'"
        :selectedComponent="currentPage"
        :selectedPage="pageName"
        :showPageFN="showPage"
      ></Login>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Home from "./components/Home";
import PopUp from "./components/PopUp";
import Registration from "./components/Registration";
import Login from "./components/Login";

export default {
  name: "App",
  data() {
    return {
      pageName: "",
      currentPage: "Home",
      lastPage: "Home",
      popUp: {
        profileImg: "",
        title: "",
        doubleRowTitle: false,
        description: "",
        btnHorizontal: false,
        btn1Text: "",
        btn1Class: "",
        btn2Text: "",
        btn2Class: ""
      }
    };
  },
  methods: {
    pageTitle(name) {
      if (name === "Registration") {
        this.namePage = "Registrace";
      } else if (name === "Login") {
        this.namePage = "Přihlásit se";
      } else if (name === "Config") {
        this.namePage = "Konfigurace";
      }
    },
    showPage(page) {
      this.currentPage = page;
      this.pageTitle(page);
    },
    showPopUp(
      profileImg,
      title,
      doubleRowTitle,
      message,
      btnHorizontal,
      btn1Text,
      btn1Class,
      btn2Text,
      btn2Class
    ) {
      this.showPage("PopUp");
      this.popUp.profileImg = profileImg;
      this.popUp.title = title;
      this.popUp.doubleRowTitle = doubleRowTitle;
      this.popUp.message = message;
      this.popUp.btnHorizontal = btnHorizontal;
      this.popUp.btn1Text = btn1Text;
      this.popUp.btn1Class = btn1Class;
      this.popUp.btn2Text = btn2Text;
      this.popUp.btn2Class = btn2Class;
    }
  },
  components: {
    Header,
    Home,
    PopUp,
    Registration,
    Login
  }
};
</script>

<style lang="scss">
@import "/public/_fonts.scss";
@import "./assets/scss/_variables.scss";
@import "./assets/scss/_mixins.scss";
@import "./assets/scss/_buttons.scss";
@import "./assets/scss/_layout.scss";
</style>
