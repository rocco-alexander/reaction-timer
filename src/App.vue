<template>
  <h1>Ninja Reaction</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <ResultsVue v-if="showResults" :reactionTime="score"/>
</template>

<script>

import Block from './components/Block.vue'
import ResultsVue from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    ResultsVue
},
  data(){
    return{
      isPlaying: false,
      showResults: false,
      delay: null,
      score: null,
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000 // 2000ms + random time between 0 and 5000ms
      this.isPlaying = true;
      this.showResults = false
    },
    endGame(reactionTime){
    this.score = reactionTime
    this.isPlaying = false
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
  color: #444;
  margin-top: 60px;
}
button{
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 5px;
  font-size: 1rem;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.3;
  cursor: not-allowed;
}
</style>

