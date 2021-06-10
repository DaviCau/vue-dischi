<template>
    <div class="main">
        <select id="type" @change="filterAlbums($event)">
            <option value="">All</option>
            <option v-for="(genre, index) in genres" :key="index" :value="genre">{{genre}}</option>
        </select>
        <div class="albums_container">
            <SingleAlbum v-for="(album, index) in albumsFiltered" :key="index" :item="album" />
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
            albums: [],
            albumsFiltered: [],
            genres: []
        }
    },
    methods:{
        filterAlbums: function(event) {
            const value = event.target.value;
            console.log(value);

            this.albumsFiltered = this.albums.filter(
                (element) => element.genre.includes(value)
            );
        }
    },
    created: function() {
        axios
            .get(this.apiUrl)
            .then((response) => {
                    this.albums = response.data.response;
                    console.log(this.albums);

                    this.albums.forEach(element => {
                        if(!this.genres.includes(element.genre)) {
                            this.genres.push(element.genre);
                        }
                    });
                    this.albumsFiltered = this.albums;
               }
            )
    } 
}
</script>

<style lang="scss" scoped>
    .main {
        height: calc(100vh - 70px);
        background-color: #1e2d3b;
        display: flex;
        flex-direction: column;
        align-items: center;

        select {
            margin-top: 20px;
        }

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