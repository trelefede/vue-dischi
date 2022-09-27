<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent :data="albums" />
  </div>
</template>

<script>

import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from './components/MainComponent.vue';

export default {
  name: 'App',
  data(){
    return {
      albums: [],
    };
  },
  // created(){
  //   console.log('recupero dati');
  //   axios
  //     .get('https://flynn.boolean.careers/exercises/api/array/music')
  //     .then((response) => {
  //       const bo = response.data;
  //       this.albums = bo.response;
  //       console.log(this.albums);
  //       // if(status === 200) {
  //       //   this.albums = data;
  //       //   console.log(this.albums);
  //       // }
  //   })
  // },
  components: {
    HeaderComponent,
    MainComponent
}
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
