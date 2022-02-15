<template>
  <ul>
    <li>{{ movie.original_title }}</li>
    <li>{{ movie.title }}</li>
    <li>
      <img  v-if="hasFlags" :src="imgFlag" :alt="movie.original_language" />
      <span v-else >
        {{ movie.original_language }}
      </span>
    </li>
    <li>{{ movie.vote_average }}</li>
  </ul>
</template>

<script>
export default {
  name: "Card",
  props: ["movie"],

  data() {
    return {
      flags: ["it", "en"],
    };
  },
  computed: {
    imgFlag() {
      return require(`../assets/img/${this.movie.original_language}.png`);
    },
    hasFlags() {
      return this.flags.includes(this.movie.original_language);
    },
   
  },
};
</script>

<style>
</style>