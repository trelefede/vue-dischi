<template>
    <div>
        <div class="row d-flex flex-wrap justify-content-center p-4">
            <div v-for="album in albums" :key="album.title" class="album-col">
                <AlbumComponent :info="album" />
            </div>
        </div>
    </div>
</template>

<!-- {
    "poster": "https:\/\/www.onstageweb.com\/wp-content\/uploads\/2018\/09\/bon-jovi-new-jersey.jpg",
    "title": "New Jersey",
    "author": "Bon Jovi",
    "genre": "Rock",
    "year": "1988"
}, -->

<script>
import AlbumComponent from "@/components/AlbumComponent.vue"

export default {
    name: 'AlbumContainerComponent',
    data(){
        return{
            searchText: '',
        }
    },
    props: {
        albums: Array
    },
    methods: {
       
    },
    components: {
        AlbumComponent,
    }
}
</script>

<style lang="scss" scoped>
.album-col{
    width: calc(100% / 5 - 20px);
    padding: 10px;
}

select{
    background-color: #1e2d3b;
    color: white;
    border: none;
    padding-left: 10px;
  }
</style>