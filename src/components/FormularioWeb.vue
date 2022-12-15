<template>
  <div class="container">
    <div v-if="(errores.length != 0)" class="alert alert-danger">
      {{mostrarErrores}}
    </div>
    <form id="formulario" @submit.prevent="validarFormulario">
      <div class="row">
        <div class="col col-8 mx-auto">
          <h1>Agregar Usuarios</h1>
          <br><br>
          <!-- Inputs Text -->
          <label for="inputNombre" class="text-start">Tu nombre</label>
          <input v-model="nombre" @keyup.space="contarPalabras" type="text" class="form-control" id="inputNombre" placeholder="Nombre completo">
          <p>Validar Nombre: <span class="fw-bold text-success">{{nombre}}</span></p>
          <br>
          <label for="inputEdad" class="form-label text-start">Edad</label>
          <input v-model.number="edad" type="number" class="form-control" id="inputEdad" placeholder="Edad">
          <p>Validar Edad: <span class="fw-bold text-success">{{edad}}</span></p>
          <br>
          <label for="inputEmail" class="form-label text-start">Email</label>
          <input v-model="email" type="email" class="form-control" id="inputEmail" placeholder="tu@email.com">
          <p>Validar Email: <span class="fw-bold text-success">{{email}}</span></p>
          <br>
          <!-- Checkbox -->
          <div class="row">
            <h4>Selecciona tu curso</h4>
            <div class="col col-2">
              <div class="form-check">
                <input v-model="cursos" class="form-check-input" type="checkbox" value="javascript" id="checkJS">
                <label class="form-check-label" for="checkJS">
                  JavaScript
                </label>
              </div>
              <div class="form-check">
                <input v-model="cursos" class="form-check-input" type="checkbox" value="react" id="checkReact">
                <label class="form-check-label" for="checkReact">
                  React
                </label>
              </div>
              <div class="form-check">
                <input v-model="cursos" class="form-check-input" type="checkbox" value="angular" id="checkNg">
                <label class="form-check-label text-start" for="checkNg">
                  Angular
                </label>
              </div>
              <div class="form-check">
                <input v-model="cursos" class="form-check-input" type="checkbox" value="vue" id="checkVue">
                <label class="form-check-label" for="checkVue">
                  Vue
                </label>
              </div>
            </div>
            <p>Validar Cursos: <span class="fw-bold text-success">{{cursos}}</span></p>
          </div>
          <br>

          <!-- Submit -->
          <div class="row">
            <div class="col-12">
              <input type="submit" class="btn btn-primary" value="ENVIAR">
            </div>
            <br>
          </div>
        </div>
      </div>
    </form>

    <div class="row mt-5">
      <h1>Listado de Usuarios</h1>
      <table-component :usuarios="usuarios" />
    </div>

  </div>
</template>

<script>
import TableComponent from './TableComponent.vue';

export default {
  name: 'FormularioWeb',
  components: {
    TableComponent
  },
  data() {
    return {
      nombre: '',
      edad: null,
      email: '',
      cursos: [],
      errores: [],
      usuarios: []
    }
  },
  methods: {
    validarFormulario(){
      if(this.nombre && this.edad && this.email){
        alert('Campos Obligatorios Ok! Enviando Formulario');

        const datos = {
          nombre: this.nombre,
          edad: this.edad,
          email: this.email,
          cursos: this.cursos
        }

        this.usuarios.push(datos);

        setTimeout(() => {
          //reset del formulario
          this.nombre = '';
          this.edad = null;
          this.email = '';
          this.cursos = [];
        }, 2000);

        return true;
      }
      if(!this.nombre){
        this.errores.push('El nombre es obligatorio!')
      }
      if(!this.edad){
        this.errores.push('La edad es obligatoria!')
      }
      if(!this.email){
        this.errores.push('El email es obligatorio!')
      }
      setTimeout(() => {
        this.errores = [];
      }, 2500);

    },
    contarPalabras(){
      console.log(('Agregando nombre'));
      this.contador++;
    },
  },
  computed: {
    mostrarErrores(){
      let misErrores = this.errores.join(" ")
      return misErrores;
    }
  },

}
</script>

<style scoped>
a {
  color: #42b983;
}
label {
  margin-left: 0.5em !important;
}
form{
  border: 1px solid lightgrey;
  border-radius: 10px;
  padding-bottom: 2rem;
}
form h1{
  margin-top: 1rem;
}
input[type="submit"]{
  padding: .5rem 3rem;
}
</style>
