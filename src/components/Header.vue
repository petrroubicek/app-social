<template>
  <header class="header">
    <button type="button" class="btn btn--icon btn--invert" @click="showBack">
      <i class="fas fa-chevron-left"></i>
    </button>
    <h1 class="header__title">{{selectedPage}}</h1>
    <button type="button" class="btn btn--icon btn--invert" @click="showPageFN('Config')">
      <i class="fas fa-cogs"></i>
    </button>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: {
    selectedComponent: String,
    selectedPage: String,
    pastComponent: String,
    showPageFN: Function
  },
  methods: {
    showBack() {
      this.selectedComponent = this.pastComponent;
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_header.scss";
</style>

