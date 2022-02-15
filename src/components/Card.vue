<template>
  <ul>
    <li v-if="item.poster_path"><img :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" :alt="item.title || item.name"></li>
    <li v-else><img src="../assets/img/placeholder.jpg" :alt="item.title || item.name"></li>
    <li>{{ item.title || item.name}}</li>
    <li>{{ item.original_title || item.name }}</li>
    <li>
      <img  v-if="hasFlags" :src="imgFlag" :alt="item.original_language" />
      <span v-else >
        {{ item.original_language }}
      </span>
    </li>
    <li>{{ voteItem }}</li>
  </ul>
</template>

<script>
export default {
  name: "Card",
  props: ["item"],

  data() {
    return {
      flags: ["it", "en"],
    };
  },
  computed: {
    imgFlag() {
      return require(`../assets/img/${this.item.original_language}.png`);
    },
    hasFlags() {
      return this.flags.includes(this.item.original_language);
    },
    voteItem(){
        return parseInt(this.item.vote_average) / 2;
    }
  },
};
</script>

<style>
</style>