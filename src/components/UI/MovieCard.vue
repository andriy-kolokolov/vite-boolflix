<template>
  <div class="card-wrapper">
    <div class="movie-title">{{ title }}</div>
  </div>
</template>

<script>
export default {
  name: "MovieCard",
  props: {
    title: {
      type: String,
      default: "Movie title missing"
    }
  }
}
</script>

<style scoped>

</style>