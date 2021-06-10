<template>
    <select name="" id="" v-model="selected" @click="selectedValue">
        <option value="">Seleziona il genere</option>
        <option value="Pop">Pop</option>
        <option value="Rock">Rock</option>
        <option value="Jazz">Jazz</option>
        <option value="Metal">Metal</option>
    </select>
</template>

<script>
export default {
    name:"Search",
    data () {
        return {
            selected : "",
        }
    },
    methods: {
    selectedValue () {
        this.$emit("selected", this.selected);
    }
  }
}
</script>

<style>

</style>