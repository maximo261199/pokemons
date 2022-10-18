<script setup>

import {useRoute, useRouter} from "vue-router";
import {useGetData} from "@/composables/getData";
import {useFavoritosStore} from  '@/store/favoritos'

const route = useRoute();
const router = useRouter();
const useFavoritos = useFavoritosStore();

const {add} = useFavoritos;

const {data, getData, loading, error} = useGetData();

const back= () =>{
router.push("/pokemons");
}

const favority = () =>{

}
getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`
);

</script>

<template>
 <p v-if="loading">Cargando informacion...</p>
<div class="alert alert-danger" v-if="error" mt-2>No esxiste el pokemon</div>
  <div v-if="data">
    <img :src="data.sprites?.front_default" alt="">
    <h1>Poke name:{{$route.params.name}}</h1>
    <button @click="add(data)" class="btn btn-outline-primary mb-2">Agregar Favorito</button>
  </div>

 <button @click="back" class="btn btn-outline-primary me-2">regresar</button>

</template>