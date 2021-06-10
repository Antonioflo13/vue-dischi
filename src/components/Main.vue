<template>
    <main>
        <section>
            <div id="flex-center" class="row">
                <div id="albums" class="col-xs-12 col-md-5 col-lg-2"
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
props: ['selected'],
components: {
    Card,
},
data() {
    return {
        api : 'https://flynn.boolean.careers/exercises/api/array/music',
        albums: [],
        loading: true,
    }
},
computed: {
    filterArtist () {
        if (this.selected == '' || this.selected == 'All') {
            newArray = this.albums
        } else {
            var newArray = this.albums.filter (
               (element) => {
                   return element.genre == this.selected
               }
            );
        }
        return newArray;
    }
},
created() {
    axios 
        .get(this.api) 
        .then(
            (response) => {
                this.albums= response.data.response;
                setTimeout(() => {
                    this.loading = false;
                    this.$emit('changeLoadingStatus', this.loading);
                    this.$emit('transferArray', this.albums);
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