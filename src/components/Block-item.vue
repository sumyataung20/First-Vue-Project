<template>
<div v-if="showBlock">
      <div class="block" @click = "stopTimer()">
    <p>Click Here {{delay}}</p>
  </div>
</div>
</template>

<script>
export default {
    props:["delay"],

    data() {
        return{
            showBlock: false,
            score: 0,
            timer: null,
        }
    },

    mounted() {
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer();
        },this.delay)
    },

    methods: {
          startTimer() {
            this.timer = setInterval(() => {
                this.score += 50
            },50)
          },

          stopTimer() {
            clearInterval(this.timer);
            console.log(this.score)
            this.$emit("endGame", this.score);
          }
    },


    updated() {
        console.log('data updated')
    },

    unmounted() {
        console.log('component unmounted')
    }

}
</script>

<style>

.block{
    background-color: aqua;
    width: 200px;
    height: 250px;
    margin: 20px auto;
    border-radius: 10px ;
    position: relative;
}
.block p{
   
   text-align: center;
   padding-top: 50%;

  
}
</style>