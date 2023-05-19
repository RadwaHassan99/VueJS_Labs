<template>
  <div id="app" :class="{ 'colored-background': !isBackgroundWhite }">
    <DataForm/>
    <button class="toggle-button" @click="toggleBackground">
      Change Theme
    </button>
  </div>
</template>

<script>
import DataForm from './components/dataForm.vue'

export default {
  name: 'App',
  components: {
    DataForm
  },
  data() {
    return {
      isBackgroundWhite: true
    }
  },
  methods: {
    toggleBackground() {
      console.log('toggleBackground method called');
      this.isBackgroundWhite = !this.isBackgroundWhite;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: white;
  transition: background-color 0.3s ease;
  color: #2c3e50;
  height: 705px;
  width: 100%;
}

.colored-background {
  background-color: rgb(54, 1, 43) !important; 
}

.toggle-button{
  border: none;
  outline: none;
  width: 20%;
  padding: 16px 10px;
  background-color: rgb(255, 252, 252);
  border-radius: 10px;
  box-shadow: 12.5px 12.5px 10px rgba(0, 0, 0, 0.015),100px 100px 80px rgba(0, 0, 0, 0.03);
  margin: 2px auto;
  margin-top: 12px;
  background-color: #8e88be;
  color: #fff;
  text-transform: uppercase;
  font-weight: bold;
  transition: background-color 0.3s ease;
}

.toggle-button:hover{
  background-color: #6d6891; 
  cursor: pointer;
}
</style>
