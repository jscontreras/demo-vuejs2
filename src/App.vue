<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
    <ais-instant-search index-name="ikea" v-bind:search-client="searchClient">
    <h1>Hello</h1>
  </ais-instant-search>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
