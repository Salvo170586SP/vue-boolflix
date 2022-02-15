<template>
  <div id="app">
    <input
      type="text"
      name="textMovie"
      id="textMovie"
      v-model="search"
      @keyup.enter="onSearch"
    />
    <button type="button" @click="onSearch">Cerca</button>

    <main>
      <div class="box-movie" v-for="(movie, id) in movies" :key="id">
        <ul>
          <li>{{ movie.original_title }}</li>
          <li>{{ movie.title }}</li>
          <li>{{ movie.original_language }}</li>
          <li>{{ movie.vote_average }}</li>
        </ul>
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",

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
          query: this.query,
          lenguage: "it_IT",
        },
      };
      axios
        .get(`https://api.themoviedb.org/3/search/movie`, config)
        .then((res) => {
          this.movies = res.data.results;
        })
    },

    onSearch(search){
      this.movies = search;
    },
    
  },
  created() {
    this.fetchMovies();
  },
};
</script>

<style lang="scss">
</style>
