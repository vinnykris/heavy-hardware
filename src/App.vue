<template>
  <div id="app">
    <img alt="Heavy Hardware Logo" src="./assets/heavy_hardware_logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Store/>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Store from './components/Store.vue'

export default {
  name: 'app',
  components: {
    //HelloWorld,
    Store
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
