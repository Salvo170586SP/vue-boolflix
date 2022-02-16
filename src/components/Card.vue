<template>
  <div class="card-item bg-dark  shadow m-1">
    <div v-if="item.poster_path">
      <img 
        :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`"
        :alt="item.title || item.name"
      />
    </div>
    <div v-else>
      <img
        class="img-default"
        src="https://www.altavod.com/assets/images/poster-placeholder.png"
        :alt="item.title || item.name"
      />
    </div>
    <div class="text-card">
      <div>{{ item.title || item.name }}</div>
      <div>{{ item.original_title || item.name }}</div>
      <div>
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
      <i v-for="n in 5" :key="n" class="fa-star" :class="n <= voteItem ? 'fa-solid' : 'fa-regular'"></i>
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
.card-item{
    cursor: pointer;
}
.w-35 {
  width: 35px;
}

/* .text-card {
    display: none;
}

.card-item > .text-card:hover{
    display: block;
} */
</style>