<template>
  <div id="app">
    <link
      href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css"
      rel="stylesheet"
    />
    <Menu v-on:showDetails="visible = !visible" />

    <Hero v-on:showDetails="visible = !visible" :visible="visible" />
    <transition name="fade">
      <Picker v-if="visible" />
    </transition>
    <Footer />
  </div>
</template>

<script>
import Picker from "./components/Picker";

import Hero from "./components/hero";
import Menu from "./components/menu";
import Footer from "./components/footer";
export default {
  name: "App",
  components: {
    Picker,
    Hero,
    Menu,
    Footer,
  },
  data() {
    return {
      visible: false,
    };
  },
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
