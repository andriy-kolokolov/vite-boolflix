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
  name: "MainResultListMovies",
  components: {MovieCard},
  data() {
    return {
      store
    }
  }
}
</script>

<style lang="sass" scoped>
@use '../assets/main' as *

$grid-cols: 6
$grid-gap: 10px

.v-enter-active,
.v-leave-active
  transition: opacity 2s ease


.v-enter-from,
.v-leave-to
  opacity: 0


.search-results-wrapper
  display: grid
  grid-template-columns: repeat($grid-cols, 1fr)
  gap: $grid-gap


@media (max-width: $md-breakpoint)
  .search-results-wrapper
    grid-template-columns: repeat(4, 1fr)

@media (max-width: $sm-breakpoint)
  .search-results-wrapper
    grid-template-columns: repeat(2, 1fr)

@media (max-width: $xs-breakpoint)
  .search-results-wrapper
    grid-template-columns: repeat(1, 1fr)


</style>