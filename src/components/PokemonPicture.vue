<template>
    <div class="pokemon-container"></div>
    <img class="hidden-pokemon" :src="imgSrc" alt="Pokemon">
    <img v-if="showPokemon" class="fade-in" :src="imgSrc" alt="Pokemon">
</template>

<script>

export default {
    props: {
        pokemonId: {
            type: Number,
            required: true
        },
        showPokemon: {
            type: Boolean,
            required: true,
            default: false
        }
    },
    computed: {
        imgSrc() {
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
        }
    }

}
</script>

<style scoped>
/* Pokemon Picture */
.pokemon-container {
    height: 200px;
}

img {
    height: 200px;
    position: absolute;
    width: 100vw;
    top: 12%;
    margin-left: -50vw;
    user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
}

.hidden-pokemon {
    filter: brightness(0);
}
</style>