<template>
  <div id="app">
    <img src="./assets/logo.png">
    <TypeGame />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import TypeGame from './components/TypeGame'

export default {
  name: 'app',
  components: {
    HelloWorld,
    TypeGame
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
