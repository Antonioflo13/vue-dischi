<template>
    <main>
        <section>
            <div v-if="filterArtist.length == 0" class="d-flex flex-column justify-content-center align-items-center">
                <img src="../assets/spotify.png" alt="logo">
                <h2>Ci spiace! La ricerca non ha popolato nessun risulato.</h2> 
            </div>
            <div id="flex-center" class="row">
                <div id="albums" class="col-xs-12 col-md-2 col-lg-2"
                v-for="(album, index) in filterArtist" :key="index">
                <Card :albums="album"/>
                </div>
            </div>
        </section>
    </main>
</template>

<script>
import Card from '../components/Card';
import axios from 'axios';

export default {
name: 'Main',
props: ['selectedGenre', 'selectedArtist'],
components: {
    Card,
},
data() {
    return {
        api : 'https://flynn.boolean.careers/exercises/api/array/music',
        albums: [],
        genres: [],
        artist: [],
        loading: true,
    }
},
computed: {
    filterArtist () {
        let finalArray = this.albums;

        if (this.selectedArtist !== 'All' && this.selectedArtist !== '') {
            finalArray = finalArray.filter (
               (element) => {
                   return element.author == this.selectedArtist
               }
            );
        }
        if (this.selectedGenre !== '' && this.selectedGenre !== 'All') {
            finalArray = finalArray.filter (
               (element) => {
                   return element.genre == this.selectedGenre
               }
            );
        }
        return finalArray;
    }
},
created() {
    axios 
        .get(this.api) 
        .then(
            (response) => {
                this.albums= response.data.response;
                this.artist= response.data.response.albums;
                this.albums.forEach(
                    (element) => {
                    if (!this.genres.includes(element.genre)) {
                        this.genres.push(element.genre);
                    }
                });
                setTimeout(() => {
                    this.loading = false;
                    this.$emit('changeLoadingStatus', this.loading);
                    this.$emit('transferArray', this.albums,this.genres);
                }, 3000);
        }
        )
}   

}
</script>

<style lang="scss" scoped>
    @import '../style/variables.scss';
    @import '../style/mixin.scss';
    main {
        height: 100vh;
        background-color: $black;
        section {
            @include wrapper;
            img {
                width: 100px;
            }
            h2 {
                color:white;
            }
        }
        #flex-center {
            justify-content: center;
        }
        #albums {
            padding: 1%;
            margin: 1%;
            background-color: $darkgrey;

        }
    }
</style>