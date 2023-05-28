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
  width: 100%;
  background-color: rgb(116, 190, 189);
}
</style>
