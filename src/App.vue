<template>
 <h1>Reaction Timer</h1>
 <button @click="start" :disabled="isPlaying">Start Playing</button>
 <Block v-if="isPlaying" :delay="delay" @end='endGame'/>
 <p v-if="isPlaying">Click on the Button When it is Visible</p>
 <Result v-if="showResults" :score="score"/>
</template>

<script>

import Block from './components/Block.vue';
import Result from './components/Result.vue';
export default {
  name: 'App',
  components:{Block,Result},
  data(){
    return {
      isPlaying:false,
      delay:null,score:null,
      showResults:false
    }
  },
  methods:{
    start(){
      this.delay=2000+Math.random()*5000,
      this.isPlaying=true,
      console.log(this.delay)
      this.showResults=false
    },
    endGame(reactionTime){
      this.score=reactionTime,
      this.isPlaying=false
      this.showResults=true
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
button{
  border: none;
  background-color: #3498db;
  padding: 12px;
  color: white;
}
</style>
