<template>
  <h3>Listado de profesores</h3>
  <p>Rellena el siguiente formulario para añadir un profesor a la tabla</p>
  <section>
    <div>
      <label>Nombre: </label><input type="text" v-model="profesor.nombre" />
    </div>
    <div>
      <label>Apellidos: </label
      ><input type="text" v-model="profesor.apellidos" />
    </div>
    <div><label>DNI: </label><input type="text" v-model="profesor.dni" /></div>
    <div>
      <label>Materias: </label><input type="text" v-model="grupoMaterias" /><button @click="agregarMateria()">Agregar materia</button>
    </div>
    <div>

    </div>
    <div>
      <label>Poner check si está entregada la documentación: </label
      ><input type="checkbox" v-model="profesor.documentacion" />
    </div>
    <button>Agregar profesor</button>
  </section>
</template>

<script setup>
import { ref } from "vue";

let profesor = ref({
  nombre: "",
  apellidos: "",
  dni: "",
  materia: [],
  documentacion: false,
});

let grupoProfesores = ref([]);

let grupoMaterias = ref('');

const agregarMateria = () => {
  profesor.value.materia.push(grupoMaterias.value);
  grupoMaterias.value = '';
}
</script>

<style scoped></style>
