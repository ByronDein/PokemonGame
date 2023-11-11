<template>
    <h1 v-if="!pokemon">Espere por favor...</h1>
    <div v-else>
        <div>
            <h1>¿Quién es este pokémon ?</h1>
            <PokemonPicture v-bind:pokemonId="pokemon.id" :showPokemon="showPokemon" />
            <PokemonOptions :pokemons="pokemonArr" />
        </div>
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
            pokemonArr: [],
            pokemon: null,
            showPokemon: false,

        }
    },
    methods: {
        async mixPoekmonArray() {
            this.pokemonArr = await getPokemonOptions()
            const rndint = Math.floor(Math.random() * (this.pokemonArr.length));
            this.pokemon = this.pokemonArr[rndint];
        }
    },
    mounted() {
        this.mixPoekmonArray();
    }
}
</script>