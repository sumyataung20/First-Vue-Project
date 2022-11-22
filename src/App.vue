<template>
  <h1>How fast can you catch me?</h1>
  <button @click="start" :disabled = "isplaying">Play</button>
 
 <div v-if="isplaying">
   <Blockitem :delay = "delay" @endGame = "endGame"/>
 </div>

 <div v-if = "end">
   <Result :score = "score"/>
 </div>


</template>

<script>

import Blockitem from "./components/Block-item.vue"
import Result from "./components/Result.vue"

export default {
  name: 'App',
  components: {
Blockitem,
Result
  },

  data() {
    return{
      isplaying: false,
      delay: null,
      score: 0,
      end: false,

    }
  },

  methods:{
    start() {
      this.isplaying = true;
      this.delay = 2000 + Math.random()*5000;
      // console.log(2000 + Math.random()*5000);
     
    },

    endGame(score) {
      this.score = score;
      this.isplaying = false;
      this.end = true;
     

    }
  }

}
</script>

<style>
#app{
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>