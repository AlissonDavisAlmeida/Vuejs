<template>
  <div class="tasks-progress rounded-pill">
      <div class="progress-bar rounded-pill progress-bar-striped bg-info progress-bar-animated" role="progressbar"  :style="{width:progress+'%'}"  aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
          {{ progress.toFixed(2) }}%
          </div>
  </div>
</template>

<script>
export default {
    props:{
        tasks : {type:Array, require:true}
    },
    data() {
        return {
          
        }
    },
    computed:{
        progress(){
           let concluidos =  this.tasks.filter(e => !e.pending)
          return  (concluidos.length/this.tasks.length) * 100 || 0
        }
    }
}
</script>

<style>
    .tasks-progress{
        display: flex;
        width: 80%;
        border: 1px solid rgba(0, 0, 255, 0.534);
        
    }
    .progress-bar{
        
    }
</style>