<template>
    <div>
        <h1>¿Quién es este pokémon ?</h1>
        <PokemonPicture v-bind:pokemonId="4" :showPokemon="true"/>
        <PokemonOptions />  
    </div>
  
</template>

<script>
import PokemonPicture from '../components/PokemonPicture.vue';
import PokemonOptions from '../components/PokemonOption.vue';
export default {
    components: {
        PokemonPicture,
        PokemonOptions
    },
}
</script>