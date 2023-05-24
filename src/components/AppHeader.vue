<template>
  <header class="header">
    <div class="header__left d-md-flex">
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
        <input type="text" class="search-field form-control rounded-3" id="search-field" placeholder="Search...">
        <div class="search-btn input-group-text">
          <i class="fa-solid fa-magnifying-glass"/>
        </div>
      </div>
      <i class="fa-regular fa-bell"></i>
      <img class="account-img" src="/account_img.png" alt="">
    </div>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
  data() {
    return {}
  }
}
</script>

<style lang="sass" scoped>
@use "../assets/main" as *

$gap-elements: 20px
$link-padding: 10px

.header
  padding-inline: 25px
  height: $header-height
  display: flex
  justify-content: space-between
  position: fixed
  inset: 0
  z-index: 50

  & > *
    height: 100%

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
  gap: $gap-elements

  i
    cursor: pointer
    transition: .2s
    padding: $link-padding

    &:hover
      opacity: .7

  .input-group-text
    color: white
    background: transparent
    border: 0

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

  .account-img
    cursor: pointer
    height: 50%
    border-radius: 10px

    &:hover
      opacity: .8

</style>