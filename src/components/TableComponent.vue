<template>
  <table class="table">
    <thead>
      <tr>
        <th scope="col">Nombre</th>
        <th scope="col">Edad</th>
        <th scope="col">Email</th>
        <th scope="col">Cursos</th>
      </tr>
    </thead>
    <tbody>
        <fila-component
        v-for="(user, index) in usuarios" :key="index"
        is="fila-component"
        :nombre="user.nombre"
        :edad="user.edad"
        :email="user.email"
        :cursos="user.cursos"/>
    </tbody>
  </table>
</template>

<script>
import FilaComponent from './FilaComponent.vue';

export default {
  name: "TableComponent",
  components:{
    FilaComponent
  },
  data() {
    return {
      usuariosRecibidos: []
    }
  },
  props: {
    usuarios: Array
  }
};
</script>

<style scoped>
</style>