<template>
  <div id="app">
    <Header />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";

export default {
  name: "App",
components:{
  Header,
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
  },
};
</script>

<style lang="scss">
</style>
