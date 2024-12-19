<template>

    <h1>
        this is a timer app
    </h1>
    <button @click="startChallenge" :disabled="isPlaying">
        Start
    </button>
    <Block v-if="isPlaying" :delay="delay" @end="EndGame"/>
    <!-- <p>
        time is {{ score }}ms
    </p> -->
    <Results  v-if="showResult" :score="score" />
</template>
<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';

  export default{
    name: 'App',
    components :{Block,Results},
    data(){
        return {
            isPlaying:false,
            delay:null,
            score:null,
            showResult:false,
        }
    },
    methods:{
        startChallenge(){
            this.delay = 2000 + Math.random()*5000
            this.isPlaying = true
            console.log(this.delay);
            this.showResult = false
            
        },
        EndGame(reactionTime){
             this.score = reactionTime
             this.isPlaying = false
             this.showResult = true
        }

    }
  }
</script>
<style>
 *{
    padding: 0;
    margin: 0;
 }
 body{
    font-family: Arial, Helvetica, sans-serif;
 }
 #app{
    margin-top: 20px;
     text-align: center;
 }
 button{
    margin-top: 20px;
    height: 5vh;
    width: 20vh;
    background-color: lightcoral;
    border: none;
    border-radius: 10px;
    box-shadow: 0 5px 10px lightgray;
    color: white;
    cursor: pointer;
 }
 button[disabled]
   {
    opacity: 0.2;
    cursor: not-allowed;
   }
</style>
