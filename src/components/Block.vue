<template>
     <div class="block" v-if="showBlock" @click="stopTimer">
        click me 
     </div>
</template>

<script>
export default {
 props:['delay'],
 data(){
     return{
        showBlock:false,
        Timer: null,
        reactionTime:0
     }
},

mounted() {
    // console.log('component mounted');
    setTimeout(() => {
        this.showBlock = true
        this.startTimer()
    }, this.delay);
},
  methods:{
     startTimer(){
       this.Timer = setInterval(()=>{
        this.reactionTime+=10
       },10)
     },
     stopTimer(){
        clearInterval(this.Timer)
        // console.log(this.reactionTime);
        this.$emit('end',this.reactionTime)
     },
  }
// updated() { 
//     console.log('component updated');
// },
// unmounted() {
//     console.log('component unmounted');
// },
}

</script>

<style>

 .block{
    width: 400px;
    border-radius: 20px;
    background-color: lightseagreen;
    text-align: center;
    padding:100px 0 ;
    margin: 40px auto;
    box-shadow: 0 5px 10px lightgray;
    color: white;
    font-size: 30px;
 }
</style>