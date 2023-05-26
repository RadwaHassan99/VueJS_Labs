<template>
  <navbarApp v-if="!$route.meta.hideNavbar"/>
  <router-view></router-view>
  </template>
  
  

<script>
import navbarApp from "./components/pages/navbar.vue"
export default {
  name: 'App',
  components: {
    navbarApp,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  background-image: url(https://img.freepik.com/free-photo/abstract-luxury-gradient-blue-background-smooth-dark-blue-with-black-vignette-studio-banner_1258-54048.jpg?w=1380&t=st=1685092570~exp=1685093170~hmac=d1bfa797305393c2ebbaf5e89b7b4d24c82926a021f652af48394857343589f0);
}
</style>
