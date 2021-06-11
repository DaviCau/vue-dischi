<template>
  <div id="app">
    <Header :genres="allGenres" @changedGenre="updateSelectedGenre" />
    <Main @genresReady="setGenres" :selectedGenre="currentGenre" />
  </div>
</template>

<script>
  import Header from "./components/Header.vue";
  import Main from "./components/Main.vue";


export default {
  name: 'App',
  data: function() {
    return {
      allGenres: [],
      currentGenre: "",
    }
  },
  methods: {
    setGenres: function(array) {
      this.allGenres = array;
    },
    updateSelectedGenre: function(newGenre) {
      this.currentGenre = newGenre;
    }
  },
  components: {
    Header,
    Main
  }
}
</script>

<style lang="scss">
  @import '~bootstrap/scss/bootstrap';
  @import '~@fontsource/roboto/index.css';
  @import '~@fontsource/roboto/700.css';

  body {
    font-family: 'Roboto', sans-serif;
  }
</style>
