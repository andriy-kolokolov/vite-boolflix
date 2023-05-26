<template>
  <div class="search-results-wrapper">
    <TransitionGroup>
      <movie-card
          v-for="(movie, i) in store.arrMovies"
          :key="i"
          :movie="movie"
      ></movie-card>
    </TransitionGroup>
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

<style lang="sass" scoped>
$grid-cols: 6
$grid-gap: 20px

.v-enter-active,
.v-leave-active
  transition: opacity 1s ease


.v-enter-from,
.v-leave-to
  opacity: 0


.search-results-wrapper
  display: grid
  grid-template-columns: repeat($grid-cols, 1fr)
  gap: $grid-gap

</style>