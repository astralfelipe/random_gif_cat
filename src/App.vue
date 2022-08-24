<template>
  <div id="app">
    <img alt="" src="">
    <Randomcat msg="Random Gif Cat"/>
  </div>
</template>

<script>
import Randomcat from './components/Randomcat'
export default {
  name: 'App',
  components: {
    Randomcat
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
body {
  background-color: lightblue;
}
</style>
