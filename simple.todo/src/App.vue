<template>
  <div id="app">
    <SimpleTodo/>
  </div>
</template>

<script>
import SimpleTodo from './components/SimpleTodo.vue'

export default {
  name: 'app',
  components: {
    SimpleTodo
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 130%;
  padding: 30px;
}
</style>
