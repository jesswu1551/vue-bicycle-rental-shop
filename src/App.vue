<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <BicycleRentalShop/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import BicycleRentalShop from './components/BicycleRentalShop.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    BicycleRentalShop,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin: auto;
  margin-top: 60px;
  width: 600px;
}
</style>
