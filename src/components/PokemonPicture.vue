<template>
  <div class="a-pokemonPicture">
    <img
      :class="{ 'a-pokemonPicture__image': true, '-show': show }"
      :src="imgSrc"
      alt="pokemon"
    />
  </div>
</template>

<script>
export default {
  name: "PokemonPicture",
  props: {
    id: {
      type: Number,
      required: true,
    },
    show: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
  computed: {
    imgSrc() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.id}.svg`;
    },
  },
};
</script>

<style scoped>
.a-pokemonPicture {
  display: flex;
  justify-content: center;
  flex-grow: 1;
  margin-bottom: 40px;
}
.a-pokemonPicture__image {
  filter: brightness(0);
  transform: scale(0.9);
  user-select: none;
  -webkit-user-drag: none;
  height: 300px;
  transition: filter 0.3s, transform 0.6s;
}
.a-pokemonPicture__image.-show {
  filter: brightness(1);
  transform: scale(1);
}
</style>
