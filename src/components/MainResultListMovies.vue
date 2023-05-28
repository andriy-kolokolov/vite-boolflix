<template>
  <transition>
    <h2 v-if="store.arrMovies.length > 1" class="p-3">Movies</h2>
  </transition>
  <div class="wrapper-results container-fluid container-xl">

    <!--    <button type="button" @click="console.log(getMoviesSec5())">TEST</button>-->
      <div v-if="store.arrMovies.length > 5" class="arrow__btn left-arrow" @click="prevSection">
        <i class="fa-sharp fa-solid fa-chevron-left"></i>
      </div>
      <div class="results">
        <TransitionGroup>
          <section id="section1" v-if="getSectionsAvailable() > 0">
            <movie-card class="card-movie" v-for="(movie, i) in getMoviesSec1()" :key="i" :movie="movie"></movie-card>
          </section>
          <section id="section2" v-if="getSectionsAvailable() > 1">
            <movie-card class="card-movie" v-for="(movie, i) in getMoviesSec2()" :key="i" :movie="movie"></movie-card>
          </section>
          <section id="section3" v-if="getSectionsAvailable() > 2 ">
            <movie-card class="card-movie" v-for="(movie, i) in getMoviesSec3()" :key="i" :movie="movie"></movie-card>
          </section>
          <section id="section4" v-if="getSectionsAvailable() > 3">
            <movie-card class="card-movie" v-for="(movie, i) in getMoviesSec4()" :key="i" :movie="movie"></movie-card>
          </section>
        </TransitionGroup>
      </div>
      <div v-if="store.arrMovies.length > 5" class="arrow__btn right-arrow" @click="nextSection">
        <i class="fa-sharp fa-solid fa-chevron-right"></i>
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
      itemsForSection: 5,
      currentSection: 1
    }
  },
  methods: {
    getMoviesSec1() {
      return this.store.arrMovies.slice(0, 5)
    },
    getMoviesSec2() {
      return this.store.arrMovies.slice(5, 10)
    },
    getMoviesSec3() {
      return this.store.arrMovies.slice(10, 15)
    },
    getMoviesSec4() {
      return this.store.arrMovies.slice(15, 20)
    },
    getSectionsAvailable() {
      return Math.ceil(store.arrMovies.length / this.itemsForSection);
    },
    nextSection() {
      const sectionsAvailable = this.getSectionsAvailable();
      if (this.currentSection < sectionsAvailable) {
        this.currentSection += 1;
      } else {
        this.currentSection = 1;
      }
      const nextSection = document.getElementById(`section${this.currentSection}`);
      nextSection.scrollIntoView({ behavior: "smooth" });
    },

    prevSection() {
      const sectionsAvailable = this.getSectionsAvailable();
      if (this.currentSection > 1) {
        this.currentSection -= 1;
      } else {
        this.currentSection = sectionsAvailable;
      }
      const prevSection = document.getElementById(`section${this.currentSection}`);
      prevSection.scrollIntoView({ behavior: "smooth" });
    },
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

.wrapper-results
  position: relative

  .arrow__btn
    position: absolute
    display: flex
    flex-direction: column
    justify-content: center
    cursor: pointer
    color: #e61b1b
    text-decoration: none
    font-size: 5em
    opacity: .7
    width: 80px
    text-align: center
    z-index: 1
    transition: .3s

    &:hover
      opacity: 1

    &.left-arrow
      top: 0
      bottom: 0
      left: 0
      //background: linear-gradient(-90deg, rgba(0, 0, 0, 0) 0%, rgb(0, 0, 0) 80%)

    &.right-arrow
      top: 0
      bottom: 0
      right: 0
      //background: linear-gradient(90deg, rgba(0, 0, 0, 0) 0%, rgb(0, 0, 0) 80%)

  .results
    display: grid
    grid-template-columns: repeat(5, 100%)
    overflow: hidden
    scroll-behavior: smooth

    section
      position: relative
      display: flex
      justify-content: space-around


</style>