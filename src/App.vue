<template>
  <h1> Test Your Reaction </h1>
  <button class="button" :disabled="play" @click="startPlay"> PLAY </button>
  <Block v-if="play" :delay="delay" @endPlay="endGame" />
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"


export default {
  name: 'App',
  components: { Block, Results }, 
   data() {
    return {
    play: false,
    delay: null,
    score: null,
    showResults: false
   } 
  },
  methods: {
    startPlay() {
    this.delay = 2000 + Math.random() * 5000
    this.play = true
    this.showResults = false
    },
    endGame(reactionTime) {
     this.score = reactionTime
     this.play = false
     this.showResults = true
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

.button {
  width: 100px;
  height: 100px;
  border-radius: 20px;
  border-width: 20px;
  border-color: rgb(100, 100, 208);
  font-size: 1.1em;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  cursor: pointer;
}

.button[disabled] {
  opacity: 0.6;
  cursor: not-allowed;
}

.button:active {
  border-color: rgb(10, 10, 102);
}

h1 {
  color: rgb(100, 100, 208);
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  font-weight: bolder;
}
</style>
