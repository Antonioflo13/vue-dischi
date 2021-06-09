<template>
    <div>
        <img :src="albums.poster" :alt="albums.titles">
        <h2> {{albums.title }} </h2>
    </div>
</template>

<script>
export default {
name: 'Card',
props: ["albums"],
}

</script>

<style lang="scss" scoped>
    img {
        width: 200px;
        height: 200px;
    }
</style>