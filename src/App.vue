<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script>
  import Block from './components/Block.vue';
  import Results from './components/Results.vue';
  export default {
    name: 'App',
    components: {Block, Results},
    data(){ 
      return{
        isPlaying: false,
        delay: null,
        score: null,
        showResults: false
        
      }
    },
    methods:{
      start(){
        this.delay = Math.ceil(2000 + Math.random() * 5000);
        this.isPlaying = true;
        this.showResults = false
      },
      endGame(endtime){
        this.score = endtime
        this.isPlaying = !this.isPlaying
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
  background-color: #0faf87;
  font-size: 2rem;
  border: none;
  border-radius: 5px;
  color: #fff;
  padding: 8px 16px;
  letter-spacing: 1px;
  margin: 10px;
  cursor: pointer;
}
button:disabled{
  opacity: 0.3;
  cursor: not-allowed;
}
</style>
