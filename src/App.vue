<template>
  <div id="app">
    <editor v-bind:content="text" v-on:update="text = $event"/>
  </div>
</template>

<script>
import Editor from './components/Editor';

export default {
  name: 'App',
  data() {
    return {
      text: '',
    }
  },
  components: {
    'editor': Editor,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 1.3em;
}
</style>
