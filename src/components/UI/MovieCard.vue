<template>
  <div class="card-wrapper">
    <img class="movie-poster-img" :src="tryGetPoster(movie.poster_path)" alt="">
    <div class="movie-info">
      <div class="movie-title">{{ movie.title }}</div>
      <div class="movie-language">{{ movie.original_language }}</div>
      <div class="movie-vote">{{ movie.vote_average }}</div>
    </div>
  </div>

</template>

<script>
export default {
  data() {
    return {
      imagesRootPath: "http://image.tmdb.org/t/p/w500", // 'w500' is for img width
      posterNotFoundImg: "/movie-poster-not-found.png"  // public dir
    }
  },
  name: "MovieCard",
  props: {
    movie: {
      type: Object,
      required: true
    }
  },
  methods: {
    tryGetPoster(posterPath) {
      return posterPath === null ? this.posterNotFoundImg : this.imagesRootPath + posterPath;
    }
  }

}
</script>

<style lang="sass" scoped>
@use '../../assets/main' as *

.card-wrapper
  position: relative
  transition: all .3s
  height: $card-height

  &:hover
    margin: 0 20px
    transform: scale(1.1)

  &:hover .movie-info
    opacity: 1

.v-enter-active,
.v-leave-active
  transition: opacity 2s ease


.v-enter-from,
.v-leave-to
  opacity: 0

.movie-info
  padding: 30px 10px
  cursor: pointer
  position: absolute
  top: 0
  left: 0
  width: 100%
  height: 100%
  background-color: rgba(0, 0, 0, 0.75)
  color: white
  opacity: 0
  transition: opacity .3s ease-in-out

.movie-poster-img
  object-fit: cover
  height: 100%
  width: 100%

</style>