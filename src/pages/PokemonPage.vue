<template>
    <h1 v-if="!pokemon">Espere por favor...</h1>
    <div v-else>
        <div>
            <h1>¿Quién es este pokémon ?</h1>
            <PokemonPicture v-bind:pokemonId="pokemon.id" :showPokemon="showPokemon" />
            <PokemonOptions :pokemons="pokemonArr" @selection="checkAnswer(1, $event)" />

            <div v-if="showAnswer">
                <h2>{{ message }}</h2>
                <h2>Score: {{ playerScore }}</h2>
                <button @click="newGame">
                    Nuevo Juego
                </button>
            </div>
        </div>
    </div>
</template>

<script>
import PokemonPicture from '../components/PokemonPicture.vue';
import PokemonOptions from '../components/PokemonOption.vue';

import getPokemonOptions from '@/helpers/getPokemonOptions';

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
            playerScore: 0,
            showAnswer: false,
            message: '',

        }
    },
    methods: {
        async mixPoekmonArray() {
            this.pokemonArr = await getPokemonOptions()
            const rndint = Math.floor(Math.random() * (this.pokemonArr.length));
            this.pokemon = this.pokemonArr[rndint];
        },
        checkAnswer(numero, selectedId) {
            this.showPokemon = true;
            this.showAnswer = true;

            if (this.pokemon.id === selectedId) {
                this.playerScore = + 1;
                this.message = `Correcto ${this.pokemon.name}`;
            }
            else {
                this.playerScore = this.playerScore;
                this.message = `Oops, era  ${this.pokemon.name}`;
            }
        },
        async newGame() {
            this.showPokemon = false;
            this.showAnswer = false;
            this.pokemon = null;
            this.message = '';
            this.playerScore = 0;
            await this.mixPoekmonArray();
    },
    },
   
    mounted() {
        this.mixPoekmonArray();
    }
}
</script>