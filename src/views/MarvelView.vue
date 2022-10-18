<script setup>
import axios from 'axios'
import {ref} from 'vue'
import {RouterLink} from 'vue-router'

const marvel = ref([]);

const  getData = async  () => {
  try{
    const {data} = await axios.get("https://gateway.marvel.com/docs/public");
    marvel.value = data.apis;
    console.log(data);
  }catch (error){
    console.log(error);
  }
}
getData()
</script>

<template>
<ul>
  <li v-for="ma in marvel">

  </li>
</ul>

</template>