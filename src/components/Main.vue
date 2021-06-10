<template>
    <main>
        <section>
            <div id="flex-center" class="row">
                <div id="albums" class="col-xs-12 col-md-5 col-lg-2"
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
        loading:true
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