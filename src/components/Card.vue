<template>
  <ul>
    <li>{{ movie.original_title }}</li>
    <li>{{ movie.title }}</li>
    <li>{{ movie.original_language }}</li>
    <li>{{ movie.vote_average }}</li>
  </ul>
</template>

<script>
export default {
  name: "Card",
  props:['movie']
};
</script>

<style>
</style>