<template>
    <header>
        <nav class="container">
            <img src="../assets/spotify.png" alt="logo">
        </nav>
        <Search @selected="updateValue"/>
    </header>
</template>

<script>
import Search from '../components/Search';
export default {
    components: {
    Search
  },
    name: 'Header',
    data () {
        return {
            selected : "",
        }
    },
    methods: {
    updateValue (playload) {
        this.selected = playload;
        this.$emit("selected", this.selected, this.albums);
    }
  }
}

</script>

<style lang="scss" scoped>
    @import '../style/variables.scss';
    header {
        background-color: $darkgrey;
    }
    nav {
        padding: 10px 0;
        img {
            width: 50px;
        }
    }
</style>