<template>
  <ul class="a-pokemonOption">
    <li
      class="a-pokemonOption__item"
      v-for="{ id, name } in pokemons"
      :key="id"
      @click="$emit('selection', id)"
    >
      <button class="a-pokemonOption__btn">{{ name }}</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: "PokemonOption",
  props: {
    pokemons: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.a-pokemonOption {
  margin: 0;
  padding: 0;
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 5px;
  width: 270px;
  margin: 0 auto;
}
.a-pokemonOption__item {
  display: flex;
}
.a-pokemonOption__btn {
  display: flex;
  flex-grow: 1;
  justify-content: center;
  align-items: center;
  background-color: #4f4f4f;
  color: #f6f6f6;
}
.a-pokemonOption__btn:hover {
  background-color: #2e2c2c;
}
</style>
