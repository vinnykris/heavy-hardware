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
import Product from './components/Product.vue';

export default {
  name: 'app',
  components: {
    //HelloWorld,
    Store,
    Product
  },
  data () {
    return {
      isModalVisible: false,
    };
  },
  methods: {
    showModal() {
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    }
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
