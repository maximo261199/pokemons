<script setup>

import {useRoute, useRouter} from "vue-router";
import {useGetData} from "@/composables/getData";

const route = useRoute();
const router = useRouter();

const {data, getData, loading, error} = useGetData();

const back= () =>{
router.push("/pokemons");
}

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`
);

</script>


<template>
 <p v-if="loading">Cargando informacion...</p>
<div class="alert alert-danger" v-if="error" mt-2>No esxiste el pokemon</div>
  <div v-if="data">
    <h1>Poke name:{{$route.params.name}}</h1>
    <img :src="data.sprites?.front_default" alt="">
  </div>

 <button @click="back" class="btn btn-outline-primary">regresar</button>
</template>