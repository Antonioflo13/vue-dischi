<template>
    <header class="d-flex">
        <nav class="container d-flex align-items-center">
            <img src="../assets/spotify.png" alt="logo">
            <Search @selected="updateValue" :genres="genres" :album="album"/>
        </nav>
    </header>
</template>

<script>
import Search from '../components/Search';
export default {
    components: {
    Search
  },
    name: 'Header',
    props: ["album", "genres"],
    data () {
        return {
            selectedGenre : "",
            selectedArtist : "",
        }
    },
    methods: {
    updateValue (genre, artist) {
        this.selectedGenre = genre;
        this.selectedArtist = artist;
        this.$emit("selected", this.selectedGenre,this.selectedArtist);
    }
  }
}

</script>

<style lang="scss" scoped>
    @import '../style/variables.scss';
    header {
        height: 20vh;
        background-color: $darkgrey;
    }
    nav {
        padding: 10px 0;
        img {
            width: 50px;
        }
    }
</style>