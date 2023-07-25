<template>

  <div class=" container-fluid">
    <transition>
      <h2 v-if="store.arrMovies.length > 1" class="pt-3 pb-3">Movies</h2>
    </transition>
    <div class="wrapper-results">
      <transition-group>
        <div v-if="store.searching">
          <h1 class="searching-txt">Searching...</h1>
        </div>
        <div v-else-if="!store.searching" class="row g-1">
          <movie-card
              class="col-sm-6 col-md-4 col-lg-2"
              v-for="movie in store.arrMovies"
              :key="movie.id"
              :movie="movie">
          </movie-card>
        </div>
      </transition-group>
    </div>
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
      store,
    }
  },
  methods: {}
}
</script>

<style lang="sass" scoped>
@use '../assets/main' as *

.v-enter-active,
.v-leave-active
  transition: opacity .5s ease

.v-enter-from,
.v-leave-to
  opacity: 0

.searching-txt
  position: absolute
  color: #fd041b
  top: 50%
  left: 50%
  transform: translate(-50%, -50%)

</style>