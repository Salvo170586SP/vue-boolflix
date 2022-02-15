<template>
  <ul>
    <li>{{ item.title }}</li>
    <li>{{ item.original_title }}</li>
    <li>
      <img  v-if="hasFlags" :src="imgFlag" :alt="item.original_language" />
      <span v-else >
        {{ item.original_language }}
      </span>
    </li>
    <li>{{ item.vote_average }}</li>
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
   
  },
};
</script>

<style>
</style>