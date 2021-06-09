<template>
    <main>
        <section>
            <div class="row">
                <div class="col-lg-3"
                v-for="(album, index) in albums" :key="index">
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
components: {
    Card
},
data() {
    return {
        api : 'https://flynn.boolean.careers/exercises/api/array/music',
        albums: [],
    }
},
created() {
    axios 
        .get(this.api) 
        .then(
            (response) => {
                this.albums= response.data.response;
                console.log(this.albums);
        }
        )
}   

}
</script>

<style lang="scss" scoped>
    @import '../style/variables.scss';
    @import '../style/mixin.scss';
    main {
        background-color: $black;
        section {
            @include wrapper;
        }
        .card {
            max-width: 200px;
            max-height:200px;

        }
    }
</style>