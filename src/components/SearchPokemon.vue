<script setup>
import DetailsPokemon from './DetailsPokemon.vue';
import { ref } from "vue";
const props = defineProps({
  pokemonsList: Array,
})
const isPokemon = ref(false);
const pokemonSelected = ref("");
const pokemonDatas = ref({});
function chercherPokemon() {
    console.log("Bouton cliqué");
    fetch("https://pokebuildapi.fr/api/v1/pokemon/" + pokemonSelected.value)
    .then(response => response.json())
  .then(pokemon => {
    console.log(pokemon);
    pokemonDatas.value = pokemon;
    isPokemon.value = true;
  })
}
</script>

<template>
    <section>
    <h1>Informations Pokemon</h1>
    <form>
        <div id="selection">
        <label for="pokemon">Choisir un Pokémon :</label>
        <select v-model="pokemonSelected" id="select-pokemon">
             <option v-for="pokemon in pokemonsList" :value="pokemon.id">
                 {{ pokemon.name }}
            </option>
            </select>
        </div>
        <div id="btn-pokemon">
        <label for="soumettre">Connaitre ses caractéristiques</label>
        <input @click.prevent="chercherPokemon" type="submit" name="soumettre" value="Go !">
        </div>
    </form>
    <DetailsPokemon v-if="isPokemon === true" :pokemonDetails="pokemonDatas"/>
   </section> 
</template>