<template>
  <div id="app">
    <div v-if="!loading" :loadings="loading" v-on:input="updateValue($event.target.props.loading)">
      <Header/>
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
      props:[{loading:true}],
    }
  },
  methods: {
    updateValue (props) {
      this.$emit('input', props.loading);
      console.log(this.$emit('input', props.loading));
    }
  }
}
</script>

<style lang="scss">
  @import './style/general.scss';
  @import './style/variables.scss';
  @import 'node_modules/bootstrap/scss/bootstrap.scss';
</style>
