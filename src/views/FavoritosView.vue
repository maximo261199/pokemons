<script setup>
import {useFavoritosStore} from  '@/store/favoritos'
import {storeToRefs} from "pinia";
import {RouterLink} from "vue-router";



const userFavoritos = useFavoritosStore();

const {favoritos} = storeToRefs(userFavoritos) ;
const {remove, masInformacion} = userFavoritos;




</script>
//destructtiva de un a referencia metodos reactivos usamos el storeToRefs

<template>
<h1>Favoritos</h1>
  <p v-if="favoritos.length === 0">Sin favoritos</p>
  <ul class="list-group" v-else>
    <li class="list-group-item"
        v-for="poke in favoritos"
        :key="poke.id"
        >
      <div>
        {{poke.name}}
      </div>
      <div>
        <button class="btn btn-sm btn-danger" @click="remove(poke.id)" >Eliminar</button>
        <router-link class="btn btn-sm btn-outline-primary me-2" :to="`/pokemons/${poke.name}`">Mas Informacion</router-link>

      </div>

    </li>
  </ul>
  <button @click="back" class="btn btn-outline-primary"> Volver</button>
</template>