<template>
    <main>
        <img src="../assets/spotify.png" alt="loader-logo">
        <img src="../assets/Ellipsis-1s-200px.svg" alt="loader">
    </main>
</template>

<script>
export default {
name: 'Loader'
}
</script>

<style lang="scss" scoped>
    @import '../style/variables.scss';
    main {
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: $black;
        img {
            width: 80px;
        }
    }
</style>