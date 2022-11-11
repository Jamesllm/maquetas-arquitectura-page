<template>
  <div id="app">
    <loading-page />
    <router-view />
  </div>
</template>

<script>
import LoadingPage from "@/components/LoadingPage.vue";

export default {
  components: {
    LoadingPage
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&display=swap");

#app {
  font-family: "Poppins", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

a {
  text-decoration: none !important;
  color: #000000 !important;
}
</style>
