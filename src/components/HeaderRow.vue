<template>
  <div class="header-container">
    <div>
      <a href="#">
        <img src="../assets/images/Chords.svg" alt="chords-logo" class="logo" />
      </a>
      <div class="nav-links">
        <router-link to="/" class="top">Buy</router-link> |
        <router-link to="/Sell" class="top">Sell</router-link>
      </div>
    </div>

    <div class="search-profile-container">
      <router-link to="/Profile" class="top">Profile</router-link> | Cart
      <div class="search">
        <input type="search" name="Search" class="search-field" />
        <button type="submit" class="search-button">
          <img src="../assets/images/search.png" alt="icon" />
        </button>
      </div>
    </div>
  </div>
  <hr />
</template>

<script>
export default {
  name: 'HeaderRow',
  data() {
    return {}
  },
}
</script>

<style lang="scss" scoped>
.header-container {
  height: auto;
  display: flex;
  justify-content: space-between;
}

.logo {
  width: 14rem;
}

.nav-links {
  margin-top: 0.75rem;
}

.search-field {
  font-size: 1rem;
  height: 2.25rem;
  width: 14rem;
  margin-top: 0.5rem;
  padding-top: 10px;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  border: 1px solid black;
  margin-bottom: 4rem;
}

.search-profile-container {
  text-align: right;
}

.search-button {
  background: transparent;
  border: none;
  outline: none;
  margin-left: -33px;
}

.search-button img {
  width: 20px;
  height: 20px;
  object-fit: cover;
}
</style>
