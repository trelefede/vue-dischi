<template>
  <main>
    <div class="container">
      <SelectComponent :options="genres" @selected="searchByGenre" />
      <SelectComponent :options="artists" @selected="searchByArtists" />
      <AlbumContainerComponent :albums="albumsToDisplay" />
    </div>
  </main>
 
</template>

<script>
import axios from "axios"

import AlbumContainerComponent from "@/components/AlbumContainerComponent.vue"
import SelectComponent from "@/components/SelectComponent.vue"

export default {
  name: "MainComponent",
  data(){
    return {
      albums: [],
      selectedGenre: 'all',
      selectedArtist: 'all'
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
    // metodo diverso per ciclare array, restituire valori
    artists(){
      const array = this.albums.map((itemArray)=> {
        return itemArray.author;
      })
      return array;
    },
    albumsToDisplay(){
      const array = [];
      this.albums.forEach((itemArray) => {
        if(this.validGenre(itemArray) & this.validArtist(itemArray)){
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
    },
    searchByArtists(artist){
      this.selectedArtist = artist;
    },
    validGenre(itemArray){
      return  itemArray.genre === this.selectedGenre || this.selectedGenre === 'all';
    },
    validArtist(itemArray){
      return itemArray.author === this.selectedArtist || this.selectedArtist === 'all';
    },
  },
  components: {
    AlbumContainerComponent,
    SelectComponent
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