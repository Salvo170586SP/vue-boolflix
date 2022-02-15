<template>
  <ul>
    <li>{{ movie.original_title }}</li>
    <li>{{ movie.title }}</li>
    <li>
      <img src="" :alt="movie.original_language" />
      <span>
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
};
</script>

<style>
</style>