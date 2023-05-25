<template>
  <div class="main-wrapper">
    <main-result-list
        class="result-list-content"

    />
  </div>
</template>

<script>
import MainResultList from "./MainResultList.vue";
import {store} from "../store.js";

export default {
  name: "AppMain",
  components: {MainResultList},
  data() {
    return {}
  }
}
</script>

<style lang="sass" scoped>
@use "../assets/main" as *

.result-list-content
  margin-top: $header-height

</style>