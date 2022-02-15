<template>
  <div id="app">
    <header>
      <Search />
    </header>
    <main>
      <div id="movie">
        <h1>MOVIE CARD</h1>
        <Card v-for="movie in movies" :key="movie.id" :item="movie" />
      </div>

    </main>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./components/Card.vue";
import Search from './components/Search.vue';

export default {
  name: "App",
  components: {
    Card,
    Search,
  },

  data() {
    return {
      movies: [],

      api_key: "52506c224db8dc42f817a52dcdd3da51",
      query: "",
      search: "",
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
        });
    },
  },
};
</script>

<style lang="scss">
</style>
