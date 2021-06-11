<template>
    <main class="d-flex flex-column align-items-center">
        <!-- <select id="type" @change="filterAlbums($event)">
            <option value="">All</option>
            <option v-for="(genre, index) in genres" :key="index" :value="genre">{{genre}}</option>
        </select> -->
        <div class="disc_container d-flex justify-content-between align-content-center flex-wrap container">
            <SingleAlbum v-for="(album, index) in filteredAlbums" :key="index" :item="album" />
        </div>
    </main>
</template>

<script>
import SingleAlbum from "./SingleAlbum.vue"
import axios from "axios";

export default {
    name: "Main",
    props: {
        selectedGenre: String
    },
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
    // methods:{
    //     filterAlbums: function(event) {
    //         const value = event.target.value;
    //         console.log(value);

    //         this.albumsFiltered = this.albums.filter(
    //             (element) => element.genre.includes(value)
    //         );
    //     }
    // },
    created: function() {
        axios
            .get(this.apiUrl)
            .then((response) => {
                    this.albums = response.data.response;
                    // console.log(this.albums);

                    this.albums.forEach(element => {
                        if(!this.genres.includes(element.genre)) {
                            this.genres.push(element.genre);
                        }
                    });
                    // this.albumsFiltered = this.albums;
                    this.$emit("genresReady", this.genres)
               }
            )
    },
    computed: {
        filteredAlbums: function() {
            if (this.selectedGenre == "") {
                return this.albums;
            }

            return this.albums.filter(
                (element) => element.genre.includes(this.selectedGenre)
            );
        }
    }
}
</script>

<style lang="scss" scoped>
    main {
        height: calc(100vh - 70px);
        background-color: #1e2d3b;

        select {
            margin-top: 20px;
        }

        .disc_container {
            height: calc(100vh - 70px);
        }
    }
</style>