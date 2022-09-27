<template>
  <main>
    <div class="container">
      <AlbumContainerComponent :albums="albums" />
    </div>
  </main>
 
</template>

<script>
import axios from "axios"

import AlbumContainerComponent from "@/components/AlbumContainerComponent.vue"

export default {
  name: "MainComponent",
  data(){
    return {
      albums: [],
    }
  },
  created(){
    axios
    .get('https://flynn.boolean.careers/exercises/api/array/music').then((response) => {
      console.log(response);
      console.log(response.data);
      this.albums = response.data.response;
    })
    .catch((e) => {
      console.log(e);
    })
  },
  components: {
    AlbumContainerComponent,
  },
}
</script>

<style lang="scss" scoped>
main{
  color: white;
  background-color: #1e2d3b;
  .container{
    height: 100vh;
  }
}
</style>