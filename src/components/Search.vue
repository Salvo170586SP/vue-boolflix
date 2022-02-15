<template>
  <div>
    <input
      type="text"
      name="textMovie"
      id="textMovie"
      v-model="searchTerm"
      @keyup.enter="emitSearch"
    />
    <button type="button" @click="emitSearch">Cerca</button>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      searchTerm: "",
    };
  },
  methods: {
    emitSearch() {
      this.$emit("search", this.searchTerm);
    },
  },
};
</script>

<style>
</style>