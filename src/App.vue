<template>
  <div id="app">
    <div v-show="!loading">
      <Header @selected="updateValue"/>
      <Main @changeLoadingStatus="changeLoading" @transferArray="array" :selected="selected"/>
    </div>
    <Loader v-show="loading"/>

  </div>
</template>

<script>
import Header from './components/Header';
import Main from './components/Main';
import Loader from './components/Loader';

export default {
  name: 'App',
  components: {
    Header,
    Main,
    Loader,
  },
  data() {
    return {
      loading: true,
      selected: "",
      album: []
    }
  },
  methods: {
    updateValue (playload) {
      this.selected = playload;
    },
    changeLoading (status) {
      this.loading = status;
    },
    array (array) {
      this.album = array;
    },
  }
}
</script>

<style lang="scss">
  @import './style/general.scss';
  @import './style/variables.scss';
  @import 'node_modules/bootstrap/scss/bootstrap.scss';
</style>
