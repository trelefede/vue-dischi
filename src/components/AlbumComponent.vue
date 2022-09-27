<template>
  <div class="card-album">
    <img class="w-100" :src="info.poster" :alt="info.title">
    <h3> {{ info.title }} </h3>
    <span> {{ info.author }} </span>
    <span> {{ info.year }} </span>
  </div>
</template>

<script>
export default {
name: "AlbumComponent",
props: {
    info: Object
}
}
</script>

<style lang="scss" scoped>
.card-album{
    display: flex;
    flex-direction:column;
    padding: 10px;
    background-color: #2e3a46;
    height: 100%;
    text-align: center;
    h3{
        color: white;
        text-transform: uppercase;
        font-size: 0.8rem;
        padding-top: 10px;
    }
    span{
        color: #707d7a;
        font-size: 0.8rem;
    }
}
</style>