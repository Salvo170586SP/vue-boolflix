<template>
  <div id="app">
    <Header @clicked="getMovies" />
    <main>
      <div class="box-movie" v-for="(movie, id) in movies" :key="id">
        <MovieCard
          :originalTitle="movie.original_title"
          :title="movie.title"
          :lenguage="movie.original_language"
          :vote="movie.vote_average"
        />
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import MovieCard from "./components/MovieCard.vue";

export default {
  name: "App",
  components: {
    Header,
    MovieCard,
  },

  data() {
    return {
      movies: [],
      apiKey: "52506c224db8dc42f817a52dcdd3da51",
      query: "",
    };
  },

  methods: {
    fetchMovies() {
      const config = {
        params: {
          apiKey: this.apiKey,
          query: this.query,
          lenguage: "it_IT",
        },
      };
      axios
        .get(`https://api.themoviedb.org/3/search/movie`, config)
        .then((res) => {
          this.movies = res.data.results;
        });
    },
    getMovies(searchMovies){
      this.query = searchMovies;
    }




  },
};
</script>

<style lang="scss">
</style>
