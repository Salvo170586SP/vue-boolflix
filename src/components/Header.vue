<template>
  <header>
      <input type="text" name="textMovie" id="textMovie" v-model="searchMovies">
      <button type="button" @click="onSearch" >Cerca</button>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data(){
        return{
            searchMovies: '',
        }
    },
    methods:{
        onSearch(){
            this.$emit('clicked', this.searchMovies);
        }
    }
}
</script>

<style>

</style>