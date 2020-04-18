<template>
  <div
    id="app"
    v-bind:class="{'body--bg-purple' : (currentSelectedPage == 'Home'), 'body--bg-gray' : (currentSelectedPage != 'Home')}"
  >
    <!-- HEADER -->
    <Header
      v-if="currentSelectedPage != 'Home'"
      :selectedComponent="currentSelectedPage"
      :goBackFN="goBack"
      :goNextFN="goNext"
    ></Header>

    <!-- CONTENT -->
    <div class="container">
      <!-- HOMEPAGE -->
      <Home
        v-if="currentSelectedPage == 'Home'"
        :selectedComponent="currentSelectedPage"
        :goNextFN="goNext"
      ></Home>

      <!-- POPUP --
      <PopUp
        v-if="currentSelectedPage == 'PopUp'"
        :selectedComponent="currentSelectedPage"
        :profileImg="popUp.profileImg"
        :title="popUp.title"
        :doubleRowTitle="popUp.doubleRowTitle"
        :message="popUp.message"
        :btnHorizontal="popUp.btnHorizontal"
        :btn1Text="popUp.btn1Text"
        :btn1Class="popUp.btn1Class"
        :btn2Text="popUp.btn2Text"
        :btn2Class="popUp.btn2Class"
        :changePageFN="changePage"
        :showPopUpFN="showPopUp"
      ></PopUp>-->
      <!-- PROCESS -->
      <Process
        v-if="currentSelectedPage == 'Process'"
        :selectedComponent="currentSelectedPage"
        :goNextFN="goNext"
      ></Process>

      <!-- REGISTRATION -->
      <Registration
        v-if="currentSelectedPage == 'Registration'"
        :selectedComponent="currentSelectedPage"
        :goNextFN="goNext"
      ></Registration>

      <!-- LOGIN -->
      <Login
        v-if="currentSelectedPage == 'Login'"
        :selectedComponent="currentSelectedPage"
        :goNextFN="goNext"
      ></Login>

      <!-- PROFIL -->
      <Profil
        v-if="currentSelectedPage == 'Profil'"
        :selectedComponent="currentSelectedPage"
        :goNextFN="goNext"
      ></Profil>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Home from "./components/Home";
import PopUp from "./components/PopUp";
import Process from "./components/Process";
import Registration from "./components/Registration";
import Login from "./components/Login";
import Profil from "./components/Profil";

export default {
  name: "App",
  data() {
    return {
      currentSelectedPage: "Home",
      lastSelectedPages: [],
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
    goNext(nextPage, currentPage) {
      this.currentSelectedPage = nextPage;
      this.lastSelectedPages.push(currentPage);
    },
    goBack() {
      let lastIndexPage = this.lastSelectedPages.length - 1;
      this.currentSelectedPage = this.lastSelectedPages[lastIndexPage];
      this.lastSelectedPages.splice(-1, 1);
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
      this.goNext("PopUp");
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
    Process,
    Registration,
    Login,
    Profil
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
