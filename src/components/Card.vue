<template>
    <div>
        <img class="mb-2" :src="albums.poster" :alt="albums.titles">
        <h4 class="mb-2 text-center"> {{ albums.title }} </h4>
        <h6 class="text-center"> {{ albums.author }} </h6>
        <h6 class="text-center"> {{ albums.year }} </h6>
    </div>
</template>

<script>
export default {
name: 'Card',
props: ["albums"],
}

</script>

<style lang="scss" scoped>
    @import '../style/variables.scss';
    img {
        width: 100%;
        height: 100%;
    }
    h4 {
        font-size: 20px;
        color: white;
    }
    h6 {
        margin-bottom: 1px;
        color: $txtgrey;
    }
</style>