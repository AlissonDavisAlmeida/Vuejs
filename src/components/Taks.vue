<template>
  <div class="task" :class="stateClass" @click="task.pending=!task.pending">
      <p>{{ task.name }}</p>
  </div>
</template>

<script>
export default {
    props:{
        task : {type:Object, required:true}
    },
    computed:{
        stateClass(){
            return { 
                pending:this.task.pending,
                done: !this.task.pending
            }
        }
    }
}
</script>

<style>
.task{
    box-sizing: border-box;
    width: 350px;
    height: 150px;
    padding: 10px;
    border-radius: 8px;
    font-size: 2rem;
    font-weight: 300px;
    cursor: pointer;
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 10px;
}
.pending{
    background-color: rgb(228, 64, 64);
    border-left: 12px solid #B73229;
    
}

.done{
    background-color: green;
    color: #DDD;
    border-left: 12px solid #0A8F08;
    text-decoration: line-through;

}
</style>