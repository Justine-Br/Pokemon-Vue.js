<script setup>
const props = defineProps({
    pokemonDetails: Object
})
</script>

<template>
    <div id="resultat">
    <h2>Détails de {{ pokemonDetails.name }}</h2>
    <img v-bind:src="pokemonDetails.image">
    <!-- <p v-for="type in pokemonDetails.apiTypes" :key="type.name">Type : {{ type.name }}</p> -->
    <p>Élement(s) : {{pokemonDetails.apiTypes.map((type)=> type.name).join(" / ") }}</p>
    <p v-if="pokemonDetails.apiEvolutions[0] !== undefined">Évolution(s) : {{ pokemonDetails.apiEvolutions.map((evolution)=> evolution.name).join(" / ")}}</p>
    <p v-else>Evolution : Aucune</p>
    <p>Points de vie : {{ pokemonDetails.stats.HP }}</p>
    <p>Attaque : {{ pokemonDetails.stats.attack }}</p>
    <p>Défense : {{ pokemonDetails.stats.defense }}</p>
    <p>Spéciale attaque : {{ pokemonDetails.stats.special_attack }}</p>
    <p>Spéciale défense : {{ pokemonDetails.stats.special_defense }}</p>
    <p>Vitesse : {{ pokemonDetails.stats.speed }}</p>
    </div>
</template>