<template>
  <div class="container">
    <h1 class="text-center">Player Score Counter</h1>
    <div class="card">
      <div class="card-body text-center">
        <h3>Player 1</h3>
        <button @click="decreaseScore(player_1)" class="btn btn-primary btn-danger" type="button" >Down</button>
        <span class="player-score">{{player_1.score}}</span>
        <button @click="increaseScore(player_1)" class="btn btn-primary btn-success" type="button" >Up</button>
      </div>

      <div class="card-body text-center">
        <h3>Player 1</h3>
        <button @click="decreaseScore(player_2)" class="btn btn-primary btn-danger" type="button" >Down</button>
        <span class="player-score">{{player_2.score}}</span>
        <button @click="increaseScore(player_2)" class="btn btn-primary btn-success" type="button" >Up</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ScoreCounter',
  props: {},
  data(){
    return{
      player_1: {
        score: 0
      },
      player_2: {
        score: 0
      }
    }
  },
  methods: {
    increaseScore(player){
      player.score += 1
    },
    decreaseScore(player){
      if (player.score > 0) {
        player.score -= 1
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.player-score {
  font-size: 4em;
}
</style>
