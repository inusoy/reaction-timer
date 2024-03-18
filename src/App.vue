<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <ResultsPage />
  <BlockComponent />
</template>

<script>
import BlockComponent from './components/BlockComponent.vue';
import ResultsPage from './components/ResultsPage.vue';

export default {
  name: 'App',
  components: {
    BlockComponent,
    ResultsPage
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
