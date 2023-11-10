<template>
    <div>
        <h1>¿Quién es este pokémon ?</h1>
        <PokemonPicture v-bind:pokemonId="4" :showPokemon="true"/>
        <PokemonOptions :pokemons="pokemonArr"/>  
    </div>
  
</template>

<script>
import PokemonPicture from '../components/PokemonPicture.vue';
import PokemonOptions from '../components/PokemonOption.vue';

import getPokemonOptions from '@/helpers/getPokemonOptions';
// getPokemonOptions();
export default {
    components: {
        PokemonPicture,
        PokemonOptions
    },
    data() {
        return {
            pokemonArr:[],

        }
    },
    methods: {
        async mixPoekmonArray() {
            this.pokemonArr = await getPokemonOptions()
            console.log(this.pokemonArr);
        }
    },
    mounted() {
        this.mixPoekmonArray();
    }
}
</script>