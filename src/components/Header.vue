<template>
  <top-menu></top-menu>
  <Menu />
  <header-hero></header-hero>
</template>

<script>
import Menu from "./HeaderComponents/HeaderMenu.vue";
import TopMenu from "./HeaderComponents/HeaderTopMenu.vue";
import HeaderHero from "./HeaderComponents/HeaderHero.vue";

export default {
  name: "Header",
  components: {
    Menu,
    TopMenu,
    HeaderHero
  },
};
</script>

<style></style>
