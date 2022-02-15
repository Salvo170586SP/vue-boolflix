<template>
  <div id="app">
    <header>
      <input
      type="text"
      name="textMovie"
      id="textMovie"
      v-model="search"
      @keyup.enter="fetchMovies"
    />
    <button type="button" @click="fetchMovies">Cerca</button>
    </header>
    
    <main>
      <Card v-for="(movie, id) in movies" :key="id" :movie="movie"/>
       
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./components/Card.vue"

export default {
  name: "App",
  components:{
    Card,
  },

  data() {
    return {
      movies: [],

      api_key: "52506c224db8dc42f817a52dcdd3da51",
      query: "",
      search:'',
    };
  },

  methods: {
    fetchMovies() {
      const config = {
        params: {
          api_key: this.api_key,
          query: this.search,
          lenguage: "it_IT",
        },
      };

      axios
        .get(`https://api.themoviedb.org/3/search/movie`, config)
        .then((res) => {
          this.movies = res.data.results;
        })
    },
  },
};
</script>

<style lang="scss">
</style>
