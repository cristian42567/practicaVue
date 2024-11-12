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
      <td>
        <ul>
          <li v-for="(elm, index) in profesor.materia" :key="index">{{ elm }}</li>
        </ul>
      </td>
    </div>
    <div>
      <label>Poner check si está entregada la documentación: </label
      ><input type="checkbox" v-model="profesor.documentacion" />
    </div>
    <button @click="agregarProfesor()">Agregar profesor</button>
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
  if (grupoMaterias.value == '') {
    alert('Debes añadir una materia')
  }else{
    profesor.value.materia.push(grupoMaterias.value);
    grupoMaterias.value = '';
  }
}

const agregarProfesor = () =>{
  
}


</script>

<style scoped></style>
