<template>
  <div id="app">
    <img style="width:100%;max-width:400px;margin-bottom:4em;margin:3em auto;display:block; "src="./assets/logo.svg">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top:50px;
}
</style>
