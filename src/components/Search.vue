<template>
    <div class="container pb-2 d-flex justify-content-end">
    <select name="" id="" class="form-select" v-model="selected" @change="selectedValue">
        <option selcted disabled value="All">Seleziona il genere</option>
        <option value="Pop">Pop</option>
        <option value="Rock">Rock</option>
        <option value="Jazz">Jazz</option>
        <option value="Metal">Metal</option>
    </select>
    </div>
</template>

<script>
export default {
    name:"Search",
    props: ["loading"],
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

<style lang="scss" scoped>
    @import '../style/variables.scss';
    select {
        background-color: $txtgrey;
        border: none;
        width: 10%;
        height: 1%;
    }
</style>