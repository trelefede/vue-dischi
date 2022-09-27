<template>
  <div class="row">
    <div v-for="album in albums" :key="album.title" class="album-col">
        <AlbumComponent :info="album" />
    </div>
  </div>
</template>

<script>
import AlbumComponent from "@/components/AlbumComponent.vue"

export default {
name: "AlbumContainerComponent",
props: {
    albums: Array
},
components: {
    AlbumComponent,
}
}
</script>

<style lang="scss" scoped>
.album-col{
    width: calc(100% / 5 - 20px);
}
</style>