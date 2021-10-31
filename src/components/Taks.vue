<template>
  <div class="task" :class="stateClass"
         @click="$emit('toggleTask',task)">
      <span @click.stop="$emit('taskDelete', task)" class="close">
          X

      </span>
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
    position: relative;
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
.pending .close{
    background-color: #B73229;
}
.done .close{
    background-color: #0A8F08;
}
.close{
    position: absolute;
    right: 10px;
    top: 10px;
    font-size: 0.9rem;
    font-weight: 600;
    height: 20px;
    width: 20px;
    border-radius: 10px;
    text-align: center;
}

.done{
    background-color: green;
    color: #DDD;
    border-left: 12px solid #0A8F08;
    text-decoration: line-through;

}
</style>