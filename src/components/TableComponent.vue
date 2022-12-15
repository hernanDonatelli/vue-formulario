<template>
  <table class="table table-striped table-bordered">
    <thead>
      <tr>
        <th scope="col">Nombre</th>
        <th scope="col">Edad</th>
        <th scope="col">Email</th>
        <th scope="col">Cursos</th>
      </tr>
    </thead>
    <tbody>
      <tr class="fila" v-for="(user, index) in usuarios" :key="index">
        <td>{{user.nombre}}</td>
        <td>{{user.edad}}</td>
        <td>{{user.email}}</td>
        <td>
            <span v-for="(curso, index) in user.cursos" :key="index">
              {{index+1}}-{{curso}}
            </span>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>

export default {
  name: "TableComponent",
  props: {
    usuarios: Array
  }
};
</script>

<style scoped>

</style>