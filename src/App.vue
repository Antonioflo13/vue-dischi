<template>
  <div id="app">
    <div v-show="!loading">
      <Header @selected="updateValue" :album="album" :genres="genres"/>
      <Main @changeLoadingStatus="changeLoading" @transferArray="array" :selectedGenre="selectedGenre" :selectedArtist="selectedArtist"/>
    </div>
    <Loader v-show="loading"/>

  </div>
</template>

<script>
import Header from './components/Header';
import Main from './components/Main';
import Loader from './components/Loader';

export default {
  name: 'App',
  components: {
    Header,
    Main,
    Loader,
  },
  data() {
    return {
      loading: true,
      selectedGenre: "",
      selectedArtist: "",
      album: [],
      genres: []
    }
  },
  methods: {
    updateValue (genre, artist) {
      this.selectedGenre = genre;
      this.selectedArtist = artist;
    },
    changeLoading (status) {
      this.loading = status;
    },
    array (album,genres) {
      this.album = album;
      this.genres = genres;
    },
  }
}
</script>

<style lang="scss">
  @import './style/general.scss';
  @import './style/variables.scss';
  @import 'node_modules/bootstrap/scss/bootstrap.scss';
</style>
