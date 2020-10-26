<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <AnalysisForm/>
  </div>
</template>

<script>
import AnalysisForm from './components/AnalysisForm.vue'

export default {
  name: 'App',
  components: {
    AnalysisForm
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
