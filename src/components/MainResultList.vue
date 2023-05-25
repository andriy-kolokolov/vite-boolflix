<template>
  <div class="search-results-wrapper">
    <movie-card
        v-for="(movie, i) in store.arrMovies"
        :key="i"
        :title="movie.title"
    ></movie-card>
  </div>
</template>

<script>
import {store} from "../store.js";
import MovieCard from "./UI/MovieCard.vue";

export default {
  name: "MainResultList",
  components: {MovieCard},
  data() {
    return {
      store
    }
  }
}
</script>

<style scoped>

</style>