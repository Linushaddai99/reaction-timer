<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay='delay' @end='endScore'/>
  <!-- <p v-if="showScore">Reaction Time: {{ score }}ms</p> -->
  <Results :score='score' v-if='showScore'/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      showScore: false,
      delay: null,
      score: null
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true,
      this.showScore = false
    },
    endScore(reactionTime){
      this.score = reactionTime
      this.isPlaying = false,
      this.showScore = true
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
  color: #444;
  margin-top: 60px;
}

button {
  background: rgb(7, 145, 7);
  border: none;
  color: white;
  padding: 10px 18px;
  border-radius: 5px;
  cursor: pointer;
  margin: 10px;
  font-size: 16px;
  letter-spacing: 1px;
}

button:disabled {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
