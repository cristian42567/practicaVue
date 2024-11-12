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
      <label>Materias: </label
      ><input type="text" v-model="grupoMaterias" /><button
        @click="agregarMateria()"
      >
        Agregar materia
      </button>
    </div>
    <div>
      <td>
        <ul>
          <li v-for="(elm, index) in profesor.materia" :key="index">
            {{ elm }}
          </li>
        </ul>
      </td>
    </div>
    <div>
      <label>Poner check si está entregada la documentación: </label
      ><input type="checkbox" v-model="profesor.documentacion" />
    </div>
    <button @click="agregarProfesor()">Agregar profesor</button>
  </section>

  <section>
    <table border="1" width="70%">
      <tr>
        <th>Nombre:</th>
        <th>Apellidos:</th>
        <th>DNI:</th>
        <th>Materias:</th>
        <th>documentación:</th>
      </tr>
      <tr v-for="index in grupoProfesores" :key="index.dni">
        <td>{{ index.nombre }}</td>
        <td>{{ index.apellidos }}</td>
        <td>{{ index.dni }}</td>
        <td>
          <ul>
            <li v-for="(elm, indice) in index.materia" :key="indice">
              {{ elm }}
            </li>
          </ul>
        </td>
        <td>
          <p v-if="index.documentacion">Documentación entregada.</p>
          <p v-else>Documentación sin entregar.</p>
        </td>
      </tr>
    </table>
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

let grupoMaterias = ref("");

const agregarMateria = () => {
  if (grupoMaterias.value == "") {
    alert("Debes añadir una materia.");
  } else {
    profesor.value.materia.push(grupoMaterias.value);
    grupoMaterias.value = "";
  }
};

const limpiarFormulario = () => {
  profesor.value.nombre = "";
  profesor.value.apellidos = "";
  profesor.value.dni = "";
  profesor.value.materia = [];
  profesor.value.documentacion = false;
};

const agregarProfesor = () => {
  if (
    profesor.value.nombre == "" ||
    profesor.value.apellidos == "" ||
    profesor.value.dni == "" ||
    profesor.value.materia.length === 0
  ) {
    alert("Debes rellenar todos los campos.");
    limpiarFormulario();
  } else {
    grupoProfesores.value.push({
      nombre: profesor.value.nombre,
      apellidos: profesor.value.apellidos,
      dni: profesor.value.dni,
      materia: profesor.value.materia,
      documentacion: profesor.value.documentacion,
    });
    limpiarFormulario();
  }
};
</script>

<style scoped></style>
