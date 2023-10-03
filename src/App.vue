<template>
  <CalculadoraImc msg="Calculadora de IMC"/>
</template>

<script>
import CalculadoraImc from './components/CalculadoraImc.vue'

export default {
  name: 'App',
  components: {
    CalculadoraImc
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
  margin-top: 60px;
}
</style>
