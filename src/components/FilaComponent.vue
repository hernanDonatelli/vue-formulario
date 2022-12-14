<template>
    <tr>
        <td>{{nombre}}</td>
        <td>{{edad}}</td>
        <td>{{email}}</td>
        <td>{{cursos}}</td>
    </tr>
</template>

<script>
    export default {
        name: 'FilaComponent',
        props: {
            nombre: String,
            edad: Number,
            email: String,
            cursos: Array,
        }
    }
</script>

<style scoped>

</style>