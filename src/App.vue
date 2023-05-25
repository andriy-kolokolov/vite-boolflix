<script setup>
import {AppHeader, AppMain} from './components/index'
</script>

<template>
  <div class="page-wrapper">
    <app-header @search="requestToAPI" />
    <app-main />
  </div>
</template>

<script>
import axios from "axios";
import {store} from "./store.js";

export default {
  data() {
    return {
      store,
    }
  },
  methods: {
    requestToAPI(searchTerm) {
      axios.get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "bbb653d61f5c4cedfff8c7fa5a6267c1",
          query: searchTerm,
          language: "it-IT"
        }
      })
          .then(response => {
                console.log(response.data.results);
                this.store.arrMovies = response.data.results;
              }
          )
          .catch(error => {
                console.error("Error requesting to API", error);
              }
          )
    },
  }
}
</script>

<style lang="sass">

</style>
