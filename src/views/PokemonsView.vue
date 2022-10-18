<script setup>
import {RouterLink} from 'vue-router'
import {useGetData} from "@/composables/getData";

const {data,loading, getData, error} = useGetData();

getData("https://pokeapi.co/api/v2/pokemon");
</script>

<template>
  <h1>Pokemons</h1>
  <p v-if="loading">Cargando informacion...</p>
  <div class="alert alert-danger" v-if="error" mt-2>{{error}}</div>
  <div v-if="data">
  <ul class="list-group">
  <li v-for="poke in data.results" class="list-group-item">
  <router-link :to="`/pokemons/${poke.name}`">
  {{poke.name}}
  </router-link>
  </li>
  </ul>

  <div class="mt-2"> 
  <button :disabled="!data.previous" class="btn btn-warning me-2" @click="getData(data.previous)">Previus</button>
  <button class="btn btn-primary" @click="getData(data.next)">Next</button>

  </div>

  </div>


</template>


