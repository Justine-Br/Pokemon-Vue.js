<script setup>
import MyHeader from './components/MyHeader.vue'
import SearchPokemon from './components/SearchPokemon.vue'
import MyFooter from './components/MyFooter.vue'
import {ref, onBeforeMount} from 'vue'
const allPokemons = ref([]);
onBeforeMount(() => {
  fetch("https://pokebuildapi.fr/api/v1/pokemon/")
  .then(response => response.json())
  .then(data => {
    allPokemons.value = data;
    console.log(allPokemons.value);
  })
})
</script>

<template>
 <MyHeader />
<main>
   <SearchPokemon :pokemonsList="allPokemons"/>
</main>
<MyFooter />
</template>

<style>
  @import url(https://fonts.googleapis.com/css2?family=Crimson+Text&family=Press+Start+2P&display=swap);
  @import url(https://fonts.googleapis.com/css2?family=Lato&display=swap);
  @import url(https://fonts.googleapis.com/css2?family=Raleway&display=swap);
  @import "./assets/css/style.css"
</style>
