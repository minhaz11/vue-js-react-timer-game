<template>
<div>
    <h1>Reaction timer</h1>
    <button class="btn" @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Result v-if="showResult" :score="score" />
    
</div>
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
      isPlaying:false,
      delay:null,
      score:null,
      showResult:false
    }
  },

methods: {
  start(){
    this.isPlaying = true,
    this.delay =2000 + Math.random() * 5000;
     this.showResult = false
  },
  endGame(reactTime) {
    this.score = reactTime;
    this.showResult = true
    this.isPlaying = true
  }
},

 
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

.btn{
  padding: 15px;
  background: rgb(42, 168, 49);
}
</style>
