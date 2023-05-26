<template>
  <div class="main-wrapper">
    <main-result-list
        class="result-list-content"

    />

  </div>
</template>

<script>
import MainResultList from "./MainResultList.vue";

export default {
  name: "AppMain",
  components: {MainResultList},
  props: {
    moviesReceived: false
  },
  data() {
    return {}
  }
}
</script>

<style lang="sass" scoped>
@use "../assets/main" as *
.main-wrapper
  padding-inline: $main-container-inline-padding
  margin-top: $header-height


</style>