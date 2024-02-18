<script>
import Block from "./components/BlockComp.vue"
import ResultsCom from "./components/ResultsCom.vue"
export default {
  name: 'App',
  components: { Block, ResultsCom },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
      console.log(this.delay);
    },
    endGame(reactionTime){
      this.score = reactionTime,
      this.isPlaying = false,
      this.showResults = true
    }
  }
}
</script>

<template>
  <div class="wrapper">
    <h1>Ninja reaction timer</h1> 
    <button @click="start" :disabled="isPlaying">play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <ResultsCom v-if="showResults" :score="score" />
  </div>
</template>

<style scoped>
*{
  font-family: "Poppins", sans-serif;
}
header {
  line-height: 1.5;
  max-height: 100vh;
}
.wrapper{
  margin:  0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}
button{
  width: 100px;
  padding: 10px 10px;
  font-size: 17px;
  color: white;
  background-color: rgb(38, 205, 38);
  border-radius: 10px;
  border: none;
  cursor: pointer;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
