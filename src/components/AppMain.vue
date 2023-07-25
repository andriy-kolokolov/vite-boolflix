<template>
  <div class="main-wrapper container-fluid">

    <main-result-list-movies
        class="result-list-content"

    />

  </div>
</template>

<script>
import MainResultListMovies from "./MainResultListMovies.vue";

export default {
  name: "AppMain",
  components: {MainResultListMovies},
  props: {
    moviesReceived: false
  },
  data() {
    return {

    }
  }
}
</script>

<style lang="sass" scoped>
@use "../assets/main" as *
.main-wrapper
  padding-inline: $main-container-inline-padding
  margin-top: $header-height


</style>