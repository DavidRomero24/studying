<script setup>
import { ref } from 'vue';

let newTask = ref('')
let total = 0
let totalCantidad = 0

let listProduct = [
  {
    name : 'Yuca',
    cantidad : 5,
    precio : 2000,
    fechaVencimiento : 4,
  },
  {
  name : 'Platano',
  cantidad : 2,
  precio : 3000,
  fechaVencimiento : 2,
  },
  {
  name : 'Papa',
  cantidad : 3,
  precio : 1500,
  fechaVencimiento : 10,
  },
]

function suma(cantidad,precio){
  total += cantidad * precio
  totalCantidad += cantidad
}

</script>

<template>
<div class="container">
  <h1 class="title">Tienda Romero</h1>
  <p class="products">{{ newTask }}</p>
  <h2 class="subtitle">Lista de Prodcutos</h2>

  <div class="task" >
    <div class="content">
      <div class="name">Nombre producto</div>
      <div class="canpre"><span class="contentCanpre">Cantidad</span><span class="contentCanpre">Precio</span></div>
    </div>
    <span  v-for="(objeto,index) in listProduct" :key="index" >
      <span class="linea" v-if="!(objeto.cantidad == 0 || objeto.fechaVencimiento == 0)" >
        <div class="nameProduct"> 
          {{ objeto.name }}           
          <span class="alert" v-if="objeto.fechaVencimiento < 5" >Esta por vencer</span> 
        </div>
        <div class="cant">
          <div class="contentCant"> {{ objeto.cantidad }} </div>
          <div class="contentCant"> {{ objeto.precio }} </div>
          <div> {{ suma (objeto.cantidad,objeto.precio) }}</div>
          
        </div>
      </span>

    </span>
    <div class="line">__________________</div>

    <div class="containerTotal">
    <div class="wordTotal">
      Total = 
      
    </div>
    <div class="total">
      <div class="contentTotal"> {{ totalCantidad }} </div>

      <div class="contentTotal"> {{ total }} </div>
    </div>
  </div>
  </div>

</div>
</template>

<style scoped>
.line{
  display: flex;
  justify-content: end;
  
}
.contentCanpre{
  margin: auto;
}
.contentCant{
  margin: auto;
}
.contentTotal{
  margin: auto;
}
.canpre{
  width: 50%;
  display: flex;
  justify-content: space-evenly;
}
.name{
  width: 50%;
  
}
.content{
  display: flex;
  font-size: 12px;
}
.containerTotal{
  display: flex;
}
.total{
  width: 50%;
  display: flex;
  justify-content: space-evenly;
}
.wordTotal{
  display: flex;
  width: 50%;
}
.cant{
  width: 50%;
  display: flex;
  justify-content: space-evenly;
}
.nameProduct{
  display: flex;
  width: 50%;
}
.alert{
  margin: auto 5px;
  opacity: 0.6;
  font-size: 8px;
  color: white;
}
.linea{
  display: flex;
}
.help{
  font-size: 8px;
  opacity: 0.6;
  margin: 0;
}

input{
  margin-top: 12px;
  border: none;
  border-radius: 3px;
  padding: 2px 6px;
  outline: none;
  width: 100%;
  box-sizing: border-box;
}

input::placeholder{
  opacity: 0.4;
}
.task{
  display: block;
  justify-content: space-between;
  background-color: #390D02;
  border-radius: 3px;
  margin-top: 1px;
  margin-bottom: 1px;
  padding: 2px 2px 1px 6px;
  
}
.container{
  color:#F2CDAC;
  padding: 6px 12px;
  background-color: #103778;
  border-radius: 8px;
  max-width: 420px;
  margin: 0 auto;
  font-family: 'Edu TAS Beginner', cursive;
}

h1{
  text-transform: uppercase;
  font-size: 18px;
  text-align: center;
  margin: 0;
  margin-top: 12px;
}

.products{
  font-size: 10px;
  margin: 0;
  text-align: center;
  opacity: 0.6;
}
</style>
