<template>
  <header class="header container-fluid">
    <div class="header__left">
      <img class="logo-img" src="/logo_netflix.png" alt="netflix logo image">

      <ul class="nav-list">
        <li class="list-item">Home</li>
        <li class="list-item">TV Shows</li>
        <li class="list-item">Movies</li>
        <li class="list-item">New & Popular</li>
        <li class="list-item">My List</li>
      </ul>
    </div>

    <div class="header__right">
      <div class="input-group">
        <input @keyup.enter="search"
               v-model="searchTerm"
               type="text"
               class="search-field form-control rounded-3"
               id="search-field"
               placeholder="Search..."
        >
        <div @click="search" class="search-btn input-group-text">
          <i class="fa-solid fa-magnifying-glass"/>
        </div>
      </div>
      <i class="fa-regular fa-bell"></i>
      <!--      <div class="dropdown">-->
      <!--        <select class="language-dropdown">-->
      <!--          <option value="en">English</option>-->
      <!--          <option value="fr">Italiano</option>-->
      <!--        </select>-->
      <!--      </div>-->
      <div class="account-img-wrapper">
        <img class="account-img" src="/account_img.png" alt="">
        <i class="m-0 fa-solid fa-caret-down"></i>
      </div>
    </div>
  </header>
</template>

<script>
import {store} from "../store.js";

export default {
  name: "AppHeader",
  data() {
    return {
      searchTerm: ''
    }
  },
  methods: {
    search() {
      if (this.searchTerm.length !== 0) {
        store.arrMovies = [];
        this.$emit('search', this.searchTerm)
        this.searchTerm = '';
      }
    },
    handleScroll() {
      if (window.pageYOffset > 50) {
        this.$el.classList.add("active");
      } else {
        this.$el.classList.remove("active");
      }
    }
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll)
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
}
</script>

<style lang="sass" scoped>
@use "../assets/main" as *

$gap-elements: 20px
$link-padding: 10px

.header
  padding-inline: $header-container-inline-padding
  height: $header-height
  display: flex
  justify-content: space-between
  position: fixed
  inset: 0
  z-index: 50
  transition: .75s

  & > *
    height: 100%

  &.active
    background-color: $body-color
    height: 60px

    .account-img-wrapper
      transition: 1s
      height: 80%

.header__left
  display: flex
  align-items: center
  gap: $gap-elements

  .logo-img
    cursor: pointer
    object-fit: contain
    height: 50%

.nav-list
  display: flex
  align-items: center
  list-style: none
  padding: 0
  margin: 0

  .list-item
    padding: $link-padding
    cursor: pointer
    transition: .2s

    &:hover
      opacity: .7

.header__right
  display: flex
  align-items: center

  i
    cursor: pointer
    transition: .2s
    padding: $link-padding

    &:hover
      opacity: .7

  .input-group
    display: flex
    gap: 10px

    .input-group-text
      color: white
      background: transparent
      border: 0
      padding: 0

    &:hover .search-field,
    &:focus-within .search-field

      width: 250px
      border: 1px solid rgba(128, 128, 128, 0.5)
      opacity: 1

    .search-field
      width: 10px
      opacity: 0
      background-color: transparent
      color: white
      outline: none
      transition: .5s

      &::placeholder
        color: white

  .account-img-wrapper
    height: 60%
    padding: $link-padding
    display: flex
    align-items: center
    transition: 1s

    i
      padding: 5px

    .account-img
      height: 100%
      object-fit: contain
      cursor: pointer
      border-radius: 5px
      transition: .3s

      &:hover
        opacity: .7

</style>