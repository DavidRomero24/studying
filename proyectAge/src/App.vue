<script setup>

import { ref } from 'vue'

let variableRefName = ref('')
let variableRefApellido = ref('')
let variableRefFecha = ref('')
let variableRefPhone = ref ('')
let edad = 0;
let dividirpor = 31536000000;
let totalEdad = 0;

function calculateAge(){

  const timeActual = new Date ()

  let newDate = new Date(variableRefFecha.value);

  edad = timeActual - newDate;

  
  totalEdad = Math.floor(edad / dividirpor);

  return totalEdad;


}
</script>

<template>

<div class="container">
  <input v-model="variableRefName" class="Nombre" type="text" placeholder="Escriba sus nombres">{{ variableRefName }}
  <input v-model="variableRefApellido" class="Apellido" type="text" placeholder="Escribas sus apellidos">{{ variableRefApellido }}
  <input v-model="variableRefFecha" class="fecha" type="date"> {{ calculateAge() }} 
  <input v-model="variableRefPhone" class="phone" type="number" placeholder="Escriba su numero de telefono">{{ variableRefPhone }}
</div>

</template>

<style scoped>
input::placeholder{
  opacity: 0.4;
}

input{
  margin-top: 12px;
  border: none;
  border-radius: 3px;
  padding: 2px 6px;
  outline: none;
  width: 50%;
  box-sizing: border-box;
}
.container{
  background-color: chocolate;
  color:#f2dcac;
  padding: 6px 12px;
  border-radius: 8px;
  max-width: 420px;
  margin: 0 auto;
  font-family: 'Edu TAS Beginner', cursive;
}
</style>