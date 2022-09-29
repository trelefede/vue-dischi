<template>
    <div>
      <select v-model="userSelection" @change="onChange">
          <option value="all">All</option>
          <option v-for="option in options" :key="option" :value="option"> {{ option }} </option>
      </select>
    </div>
  </template>
  
  <script>
  export default {
    name: "SelectComponent",
    data(){
      return{
        userSelection: ''
      }
    },
    props: {
        options: Array
    },
    methods: {
      onChange(){
        console.log(this.userSelection);
        this.$emit('selected', this.userSelection);
      }
    }
  }
  </script>
  
  <style lang="scss" scoped>
  
  </style>