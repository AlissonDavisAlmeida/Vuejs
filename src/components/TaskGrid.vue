<template>
  <div class="tasks">
      
      <template v-if="tasks.length">
          <Task v-for="(task, index) in tasks" :key="task.name" 
                @taskDelete="$emit('taskDelete',index )" 
                :task="task" @toggleTask="$emit('toggleTask',index)">
           
          </Task>
      </template>
      <template v-else>
          
          <p>Sua vida está em dia!</p>    
        
      </template>
  </div>
</template>

<script>
import Task from './Taks.vue'
export default {
    components:{Task},
    props:{
        tasks : {type:Array, require:true}
    }
}
</script>

<style>
    .tasks{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }
</style>