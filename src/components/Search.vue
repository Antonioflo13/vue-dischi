<template>
    <div class="container pb-2 d-flex justify-content-end">
    <select name="" id="" class="form-select" v-model="selectedGenre" @change="selectedValue">
        <option selcted disabled value="All" >Seleziona il genere</option>
        <option v-for="(genre,index) in genres" :key="index" :value="genre">{{genre}}</option>
    </select>
    <select name="" id="" class="form-select" v-model="selectedArtist" @change="selectedValue">
        <option selcted disabled value="All" >Seleziona Artista</option>
        <option v-for="(album,index) in album" :key="index" :value="album.author">{{album.author}}</option>
    </select>
    </div>
</template>

<script>
export default {
    name:"Search",
    props: ['album',"genres"],
    data () {
        return {
            selectedGenre : "",
            selectedArtist : "",
        }
    },
    methods: {
    selectedValue () {
        this.$emit("selected", this.selectedGenre, this.selectedArtist);
    }
  }
}
</script>

<style lang="scss" scoped>
    @import '../style/variables.scss';
    select {
        width: 20%;
        height: 1%;
        margin: 1%;
        border: none;
        background-color: $txtgrey;
    }
</style>