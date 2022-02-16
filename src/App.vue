<template>
  <div id="app">
    <header class="bg-dark py-3 position-fixed w-100">
      <div class="container d-flex justify-content-between align-items-center">
        <h1 class="text-danger">BOOLFLIX</h1>
        <Search @search="search" />
      </div>
    </header>

    <main class="container">
      <div id="movie" class="d-flex flex-wrap justify-content-center">
        <h2>FILM</h2>
        <Card v-for="movie in movies" :key="movie.id" :item="movie" />
      </div>
      <div id="serie tv" class="d-flex flex-wrap justify-content-center my-5">
        <h2>SERIE TV</h2>
        <Card v-for="serie in series" :key="serie.id" :item="serie" />
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./components/Card.vue";
import Search from "./components/Search.vue";

export default {
  name: "App",
  components: {
    Card,
    Search,
  },

  data() {
    return {
      movies: [],
      series: [],

      api: {
        language: "it-IT",
        baseUri: "https://api.themoviedb.org/3",
        key: "52506c224db8dc42f817a52dcdd3da51",
        uriImg: "https://image.tmdb.org/t/p/",
      },
    };
  },

  methods: {
    search(searchTerm) {
      if (!searchTerm) {
        this.movies = [];
        this.series = [];
        return;
      }
      const { key, lenguage } = this.api;

      const config = {
        params: {
          api_key: key,
          query: searchTerm,
          lenguage,
        },
      };
      this.fetchApi("search/movie", config, "movies");
      this.fetchApi("search/tv", config, "series");
    },

    fetchApi(endpoint, config, target) {
      axios.get(`${this.api.baseUri}/${endpoint}`, config).then((res) => {
        this[target] = res.data.results;
      });
    },
  },
};
</script>

<style lang="scss" >
@import "./assets/scss/style.scss";

body {
  background-color: #434343;
  color: white;
}

header {
  z-index: 1;
}

main {
  padding-top: 110px;
}

ul {
  list-style-type: none;
}
h2 {
  width: 100%;
  text-align: center;
}
</style>
