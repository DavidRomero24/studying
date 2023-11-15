<script setup>
let valorFraccion = 2000
let total = 0
let totalIngresos = 0
let no = "no"
let si = "si"
let PESADO = "pesado"
let AUTOMOVIL = "automovil"
let MOTOCICLETA = "motocicleta"

function multiplication(tiempo,valorFraccion){
  total = tiempo * valorFraccion
  totalIngresos+= total

}

let listVehiculos = [
  {
    Vehiculo : 'carro',
    Categoria : 'automovil',
    tiempo : 2,
    seEncuenta : 'no',
  },
  {
    Vehiculo : 'camion',
    Categoria : 'pesado',
    tiempo : 4,
    seEncuenta : 'no',
  },
  {
    Vehiculo : 'moto',
    Categoria : 'motocicleta',
    tiempo : 7,
    seEncuenta : 'si',
  },
  {
    Vehiculo : 'carro',
    Categoria : 'automovil',
    tiempo : 2,
    seEncuenta : 'si',
  },
  {
    Vehiculo : 'moto',
    Categoria : 'motocicleta',
    tiempo : 6,
    seEncuenta : 'no',
  }
]
</script>

<template>
  <div class="container">
    <h1>Parqueadero Exotico</h1>

    <div class="indication">
      <div class="contenido">Vehiculo</div>
      <div class="contenido">Categoria</div>
      <div class="contenido">Fraccion X 15min</div>
      <div class="contenido">
        <span class="par">Se encuentra</span>
      </div>
    </div>

    <div  v-for="(objeto,index) in listVehiculos" :key="index" >
      <div class="task" v-if="!(objeto.seEncuenta == no)">
        <div class="tipo">
          {{ objeto.Vehiculo }}
        </div>
        <div class="cat">
          {{ objeto.Categoria }}
        </div>
        <div class="time">
          {{ objeto.tiempo }}
        </div>
        <div class="parqueo"  >
          <div class="esta" > {{ objeto.seEncuenta }} </div>
        </div>
      </div>
    </div>

    <h1 class="titleCats">- Categoria Pesada</h1>

    <div class="indication">
      <div class="contenido">Vehiculo</div>
      <div class="contenido">Fraccion X 15min</div>
      <div class="contenido2">
        <span class="par">Se encuentra</span>
      </div>
    </div>
    
    <div class="listaNoEstan">
      <div v-for="(objeto,index) in listVehiculos" :key="index" >
        <div v-if="(objeto.Categoria == PESADO)">
          <div class="task" v-if="!(objeto.seEncuenta == no)">
            <div class="tipo">
              {{ objeto.Vehiculo }}
            </div>
            <div class="cat" v-if="!(objeto.seEncuenta == si)">
              {{ objeto.Categoria }}
            </div>
            <div class="time">
              {{ objeto.tiempo }}
            </div>
            <div class="parqueo"  >
              <div class="esta" > {{ objeto.seEncuenta }} </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <h1 class="titleCats">- Categoria Vehiculos</h1>
    <div class="indication">
      <div class="contenido">Vehiculo</div>
      <div class="contenido">Fraccion X 15min</div>
      <div class="contenido2">
        <span class="par">Se encuentra</span>
      </div>
    </div>
    
    <div class="listaNoEstan">
      <div v-for="(objeto,index) in listVehiculos" :key="index" >
        <div v-if="(objeto.Categoria == AUTOMOVIL)">
          <div class="task" v-if="!(objeto.seEncuenta == no)">
            <div class="tipo">
              {{ objeto.Vehiculo }}
            </div>
            <div class="cat" v-if="!(objeto.seEncuenta == si)">
              {{ objeto.Categoria }}
            </div>
            <div class="time">
              {{ objeto.tiempo }}
            </div>
            <div class="parqueo"  >
              <div class="esta" > {{ objeto.seEncuenta }} </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <h1 class="titleCats">- Categoria Motocicleta</h1>
    <div class="indication">
      <div class="contenido">Vehiculo</div>
      <div class="contenido">Fraccion X 15min</div>
      <div class="contenido2">
        <span class="par">Se encuentra</span>
      </div>
    </div>
    
    <div class="listaNoEstan">
      <div v-for="(objeto,index) in listVehiculos" :key="index" >
        <div v-if="(objeto.Categoria == MOTOCICLETA)">
          <div class="task" v-if="!(objeto.seEncuenta == no)">
            <div class="tipo">
              {{ objeto.Vehiculo }}
            </div>
            <div class="cat" v-if="!(objeto.seEncuenta == si)">
              {{ objeto.Categoria }}
            </div>
            <div class="time">
              {{ objeto.tiempo }}
            </div>
            <div class="parqueo"  >
              <div class="esta" > {{ objeto.seEncuenta }} </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <h1 class="title2">Lista de vehiculos que no estan en el parqueadero</h1>


    <div class="indication">
      
      <div class="contenido">Vehiculo</div>
      <div class="contenido">Fraccion X 15min</div>
      <div class="contenido2">
        <span class="par">Se encuentra</span>
        <span class="val">Valor Parqueo</span>
      </div>
    </div>

    <div class="listaNoEstan">

      <div v-for="(objeto,index) in listVehiculos" :key="index">
        <div class="task" v-if="!(objeto.seEncuenta == si)">
          <div class="tipo">
            {{ objeto.Vehiculo }}
          </div>
          <div class="cat" v-if="!(objeto.seEncuenta == no)">
            {{ objeto.Categoria }}
          </div>
          <div class="time">
            {{ objeto.tiempo }}
          </div>
          <div class="parqueo"  >
            <div class="esta" > {{ objeto.seEncuenta }} </div>
            <div> {{ multiplication (objeto.tiempo,valorFraccion) }} </div>
            <div class="price" > {{ total }} </div>
            

          </div>
        </div>
      </div>

      <div class="total">
        <p class="">Total Ingresos = </p>
        <p class=""> {{ totalIngresos }}</p>
      </div>
    </div>
    
  </div>
</template>

<style scoped>
.total{
  display: flex;
  font-size: 14px;
  background-color: #390D02;
  border-radius: 3px;
  margin-top: 8px;
  margin-bottom: 10px;
  padding: 2px 2px 1px 6px;
  text-align: start;
}
.titleCats{
  font-size: 10px;
  text-align: start;
}
.title2{
  font-size: 10px;
}
.price{
  width: 50%;
  font-size: 14px;
}
.esta{
  width: 50%;

}
.val{
  width: 50%;
  margin-right: 3px;
  background-color: #390D02;
  border-radius: 3px;
}
.par{
  margin-right: 3px;
  background-color: #390D02;
  border-radius: 3px;
}
.parqueo{
  width: 25%;
  text-align: center;
  display: flex;
}
.time{
  width: 25%;

}
.cat{
  width: 25%;

}
.tipo{
  width: 25%;
}
.contenido2{
  width: 25%;
  text-align: center;
  font-size: 8px;
  display: flex;
}
.contenido{
  width: 25%;
  
  text-align: center;
  font-size: 10px;
  background-color: #390D02;
  border-radius: 3px;
  margin-right: 3px;
}
.task{
  display: flex;
  background-color: #390D02;
  border-radius: 3px;
  margin-top: 8px;
  margin-bottom: 1px;
  padding: 2px 2px 1px 6px;
  text-align: center;
}

.indication{
  display: flex;
  background-color: #c52f05;
  border-radius: 3px;
  margin-top: 12px;
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
</style>
