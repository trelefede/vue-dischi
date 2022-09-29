<template>
  <main>
    <div class="container">
      <SearchComponent :options="genres" @selectedGenre="searchByGenre" />
      <AlbumContainerComponent :albums="albumsToDisplay" />
    </div>
  </main>
 
</template>

<script>
import axios from "axios"

import AlbumContainerComponent from "@/components/AlbumContainerComponent.vue"
import SearchComponent from "@/components/SearchComponent.vue"

export default {
  name: "MainComponent",
  data(){
    return {
      albums: [],
      selectedGenre: 'all'
    }
  },
  computed:{
    genres(){
      const array = [];
      this.albums.forEach(itemArray => {
        if(!array.includes(itemArray.genre)){
          array.push(itemArray.genre);
        }
      });
      return array
    },
    albumsToDisplay(){
      const array = [];
      this.albums.forEach((itemArray) => {
        if(itemArray.genre === this.selectedGenre || this.selectedGenre === 'all'){
          array.push(itemArray);
        }
      }) 
      return array;
    }
  },
  created(){
      axios
      .get('https://flynn.boolean.careers/exercises/api/array/music').then((response) => {
        console.log(response);
        console.log(response.data);
        this.albums = response.data.response;
      })
      .catch((error) => {
        console.log(error);
      })
  },
  methods: {
    searchByGenre(genre){
      this.selectedGenre = genre;
    }
  },
  components: {
    AlbumContainerComponent,
    SearchComponent
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