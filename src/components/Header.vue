<template>
    <header class="d-flex align-items-center justify-content-between px-4">
        <img src="../assets/img/spotify.png">
        <select id="type" v-model="selectedGenre" @change="$emit('changedGenre', selectedGenre)">
            <option value="">All</option>
            <option v-for="(genre, index) in genres" :key="index" :value="genre">{{genre}}</option>
        </select>
    </header>
</template>

<script>
export default {
    name: "Header",
    props: {
        "genres": Array
    },
    data: function() {
        return {
            selectedGenre: ""
        }
    }
}
</script>

<style lang="scss" scoped>
    header {
        height: 70px;
        background-color: #2e3a46;

        img {
            height: 50px;
        }
    }
</style>