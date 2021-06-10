<template>
  <div id="app">
    <div v-if="!loading">
      <Header @selected="updateValue"/>
      <Main/>
    </div>
    <Loader v-else />

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
    Loader

  },
  data() {
    return {
      loading: false,
      selected: ""
    }
  },
  methods: {
    updateValue (playload) {
      this.selected = playload;
    }
  }
}
</script>

<style lang="scss">
  @import './style/general.scss';
  @import './style/variables.scss';
  @import 'node_modules/bootstrap/scss/bootstrap.scss';
</style>
