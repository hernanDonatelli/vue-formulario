<template>
  <div id="app">
    <formulario-web/>
  </div>
</template>

<script>
import FormularioWeb from './components/FormularioWeb.vue';

export default {
  name: 'App',
  components: {
    FormularioWeb
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
#app .img-form{
  max-width: 10%;
}
</style>
