<template>
  <h1 v-if="!pokemon">Espere porfavor...</h1>

  <template v-else>
    <h1>¿Quien es ese pokemon?</h1>
    <PokemonPicture :id="pokemon.id" :show="showPokemon" />
    <PokemonOption :pokemons="pokemonArr" @selection="checkAnswer($event)" />
    <template v-if="showAnswer">
      <h2>{{ message }}</h2>
      <button @click="newGame">Nuevo juego</button>
    </template>
  </template>
</template>
<script>
import PokemonPicture from "../components/PokemonPicture.vue";
import PokemonOption from "../components/PokemonOption.vue";

import getPokemonOptions from "../helpers/getPokemonOptions";

console.log(getPokemonOptions());
export default {
  name: "PokemonPages",
  components: {
    PokemonPicture,
    PokemonOption,
  },
  data() {
    return {
      pokemonArr: [],
      pokemon: null,
      showPokemon: false,
      showAnswer: false,
      message: "",
    };
  },
  methods: {
    async mixPokemonArray() {
      this.pokemonArr = await getPokemonOptions();

      const rndInt = Math.floor(Math.random() * 4);

      this.pokemon = this.pokemonArr[rndInt];
    },
    checkAnswer(pokemonId) {
      this.showPokemon = true;
      this.showAnswer = true;
      pokemonId === this.pokemon.id
        ? (this.message = `Correcto, ${this.pokemon.name}`)
        : (this.message = `Oops, era ${this.pokemon.name}`);
    },
    newGame() {
      this.showPokemon = false;
      this.showAnswer = false;
      this.pokemon = null;
      this.mixPokemonArray();
    },
  },
  mounted() {
    this.mixPokemonArray();
  },
};
</script>
