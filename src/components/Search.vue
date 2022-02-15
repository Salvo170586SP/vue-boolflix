<template>
  <div>
    <div class="input-group mb-3 ">
      <input
        type="text"
        name="textMovie"
        id="textMovie"
        class="form-control"
        v-model="searchTerm"
        @keyup.enter="emitSearch"
      />
      <button type="button" class="btn btn-danger" @click="emitSearch">
        Cerca
      </button>
    </div>
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