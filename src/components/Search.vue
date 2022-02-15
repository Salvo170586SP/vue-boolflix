<template>
  <div>
    <input
      type="text"
      name="textMovie"
      id="textMovie"
      v-model="search"
      @keyup.enter="emitSearch"
    />
    <button type="button" @click="emitSearch">Cerca</button>
  </div>
</template>

<script>
export default {
  name: "Search",
  methods:{
    
  }
};

</script>

<style>
</style>