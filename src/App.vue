<template>
  <div
    id="app"
    v-bind:class="{'body--bg-purple' : (currentSelectedPage == 'Home'), 'body--bg-gray' : (currentSelectedPage != 'Home'), 'dark-theme' : darkMode}"
  >
    <!-- HEADER -->
    <header>
      <Header
        v-if="currentSelectedPage != 'Home'"
        :selectedComponent="currentSelectedPage"
        :goBackFN="goBack"
        :goNextFN="goNext"
      ></Header>
    </header>

    <!-- CONTENT -->
    <main class="container">
      <!-- HOMEPAGE -->
      <Home
        v-if="currentSelectedPage == 'Home'"
        :selectedComponent="currentSelectedPage"
        :goNextFN="goNext"
        :onDarkMode="darkMode"
        @update-dark-mode="updateDarkMode"
      ></Home>
      
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
    </main>
  </div>
</template>

<script>
import Header from "./components/Header";
import Home from "./components/Home";
import Process from "./components/Process";
import Registration from "./components/Registration";
import Login from "./components/Login";
import Profil from "./components/Profil";

export default {
  name: "App",
  data() {
    return {
      darkMode: false,
      currentSelectedPage: "Home",
      lastSelectedPages: []
    };
  },
  methods: {
    goNext(nextPage, currentPage) {
      this.currentSelectedPage = nextPage;
      this.lastSelectedPages.push(currentPage);
      document.body.scrollTop = 0;
      document.documentElement.scrollTop = 0;
    },
    goBack() {
      let lastIndexPage = this.lastSelectedPages.length - 1;
      this.currentSelectedPage = this.lastSelectedPages[lastIndexPage];
      this.lastSelectedPages.splice(-1, 1);
      document.body.scrollTop = 0;
      document.documentElement.scrollTop = 0;
    },
    updateDarkMode(mode) {
      this.darkMode = mode;
    }
  },
  components: {
    Header,
    Home,
    Process,
    Registration,
    Login,
    Profil
  }
};
</script>

<style lang="scss">
@import "/public/_fonts.scss";
@import "./assets/scss/config/_buttons.scss";
@import "./assets/scss/config/_layout.scss";
</style>
