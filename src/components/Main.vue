<template>
    <div class="main">
        <div class="albums_container">
            <SingleAlbum v-for="(album, index) in albums" :key="index" :item="album" />
        </div>
    </div>
</template>

<script>
import SingleAlbum from "./SingleAlbum.vue"
import axios from "axios";

export default {
    name: "Main",
    components: {
        SingleAlbum
    },
    data: function() {
        return {
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            albums: []
        }
    },
    created: function() {
        axios
            .get(this.apiUrl)
            .then((response) => {
                    this.albums = response.data.response;
                    console.log(this.albums);
               }
            )
    } 
}
</script>

<style lang="scss" scoped>
    .main {
        height: calc(100vh - 70px);
        background-color: #1e2d3b;

        .albums_container {
            height: calc(100vh - 70px);
            width: 60%;
            margin: auto;
            display: flex;
            justify-content: space-between;
            align-content: center;
            flex-wrap: wrap;
        }
    }
</style>