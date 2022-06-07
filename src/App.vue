<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld 
      :msg="msg"/>
    <RevoGrid />  
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import RevoGrid from './components/RevoGrid.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    RevoGrid
  },
  data () {
    return {
    msg: 'Ternure68'
    }
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
