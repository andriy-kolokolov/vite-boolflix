<template>
    <div class="card-wrapper">
      <img class="movie-poster-img" :src="imagesRootPath + movie.poster_path" alt="">
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
      imagesRootPath: "http://image.tmdb.org/t/p/w500"
    }
  },
  name: "MovieCard",
  props: {
    movie: {
      type: Object,
      required: true
    }
  },

}
</script>

<style lang="sass" scoped>


</style>