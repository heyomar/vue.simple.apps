<template>
  <div id="app">
    <ScoreCounter />
  </div>
</template>

<script>
import ScoreCounter from './components/ScoreCounter.vue'

export default {
  name: 'app',
  components: {
    ScoreCounter
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
