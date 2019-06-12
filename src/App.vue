<template>
  <div id="app">
    <img alt="Heavy Hardware Logo" src="./assets/heavy_hardware_logo.png">
    <Store/>
  </div>
</template>

<script>

import Store from './components/Store.vue'

export default {
  name: 'app',
  components: {
    Store,
  },
  data () {
    return {
      
    };
  },
  methods: {
  },
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
