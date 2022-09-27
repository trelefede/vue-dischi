<template>
  <header>
    <img src="../assets/img/Spotify_App_Logo.svg" alt="logo">
  </header>
</template>

<script>
export default {
    name: "HeaderComponent",
}
</script>

<style lang="scss" scoped>
header{
  height: 70px;
  padding: 10px;
  background-color: #2e3a46;
  img{
    height: 50px;
    border-radius: 30px;
  }
}
</style>