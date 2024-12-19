<template @result="ShowResult" >
    <div class="Results">
       <p class="time">
        time is {{ score }} ms
       </p>
       <p class="rank">
        {{ rank }}
       </p>
    </div>
</template>

<script >
    
   export default{
    data() {
        return {
            rank:null
        }
    },
       props: ['score'],
       mounted() {
         if (this.score <259) {
             this.rank = 'ninja fingers'
         } else if (this.score < 400 ) {
            this.rank = 'nice reflexes'
         }else{
            this.rank = 'slow reflex snail movment'
         }
       },
   }
</script>

<style scoped>
.time{
    margin-top: 10px;
}
  .rank{
    margin-top: 10px;
    font-size: 1.4em;
    color: green;
    font-weight: bold;
    
  }
</style>