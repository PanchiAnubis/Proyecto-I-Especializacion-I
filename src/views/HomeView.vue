/* eslint-disable */
<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/trolley (1).png">
    <HelloWorld msg="Lista de compras"/>
    <h1>Test</h1>

    <b-row class="mt-5">
      <b-col cols="12" md="6">
        <p>Nombre</p>
        <b-form-input type="text" v-model="nuevaFruta" v-on:keyup.enter="agregarFruta"></b-form-input>
      </b-col>
      
      <b-col cols="12" md="6">
        <p>Cantidad</p>
        <b-form-input type="number" v-model.number="cantidadFruta" v-on:keyup.enter="agregarFruta"></b-form-input>
      </b-col>

    </b-row>
    <br>
    <b-button variant="success" v-on:click="agregarFruta">Agregar</b-button> <!--v-on: se puede cambiar por @-->

    <ul class="mt-5">
      <li v-for="fruta of frutas" v-bind:key="fruta">
        <b-button variant="danger" @click="fruta.cantidad--"> - </b-button>
        {{fruta.nombre}} - {{fruta.cantidad}}
        <b-button variant="success" @click="fruta.cantidad++"> + </b-button>
        <span v-if="fruta.cantidad===0"> Selecciona una cantidad</span>
      </li>
    </ul>

  </div>
</template>

<script>
/* eslint-disable */
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  data(){
    return{
      frutas: [{nombre: 'Manzana', cantidad: 0},
        {nombre: 'Pera', cantidad: 5},
        {nombre: 'Uva', cantidad: 2}],
        nuevaFruta: '',
        cantidadFruta: ''
    }
  },
  methods:{
    agregarFruta(){
      //this para acceder a datos de data
      this.frutas.push({
        nombre: this.nuevaFruta, cantidad: this.cantidadFruta
      });
      this.nuevaFruta='';
      this.cantidadFruta= null;
    }
  }
}


</script>


