<template>
    <header>
        <nav class="container">
            <img src="../assets/spotify.png" alt="logo">
        </nav>
    </header>
</template>

<script>
export default {
name: 'Header',
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