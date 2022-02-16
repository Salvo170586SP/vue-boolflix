<template>
  <div class="card-item shadow m-1">
    <img
      class="img-cover"
      v-if="item.poster_path"
      :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`"
      :alt="item.title || item.name"
    />
    <img
      class="img-cover"
      v-else
      src="https://www.altavod.com/assets/images/poster-placeholder.png"
      :alt="item.title || item.name"
    />
    <div class="text-card p-3">
      <div class="mb-1">TITOLO: <span class="ms-1">{{ item.title || item.name }}</span></div>
      <div class="mb-1">TITOLO ORIGINALE: {{ item.original_title || item.name }}</div>
      <div class="mb-1">LINGUA: 
        <img
          class="w-35"
          v-if="hasFlags"
          :src="imgFlag"
          :alt="item.original_language"
        />
        <span v-else>
          {{ item.original_language }}
        </span>
      </div>
      <div>VOTO: 
         <i 
        v-for="n in 5"
        :key="n"
        class="fa-star mb-1"
        :class="n <= voteItem ? 'fa-solid' : 'fa-regular'"
      ></i>
      </div>
     
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["item"],

  data() {
    return {
      flags: ["it", "en"],
    };
  },
  computed: {
    imgFlag() {
      return require(`../assets/img/${this.item.original_language}.png`);
    },
    hasFlags() {
      return this.flags.includes(this.item.original_language);
    },
    voteItem() {
      return Math.round(this.item.vote_average / 2);
    },
  },
};
</script>

<style lang="scss" >
.card-item {
  position: relative;
  background: black;
  border: 3px solid white;
  height: 500px;
  cursor: pointer;
}
.w-35 {
  width: 35px;
}

img {
  height: 100%;
}

.text-card {

  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  text-align: start;
  display: none;
}

.card-item:hover > .text-card {
  opacity: 1;
  display: block;
}

.card-item:hover .img-cover{
  transition: 0.3s;
  opacity: 0.1;
}
</style>