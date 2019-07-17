<template>
  <div id="app" @keyup.48.49.50.51.52.53.54.55.56.57="alertt">
    <img alt="Vue logo" src="./assets/logo.png">
    <calculator/>
  </div>
</template>

<script>
import calculator from './components/calculator.vue'

export default {
  name: 'app',
  components: {
    calculator
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
