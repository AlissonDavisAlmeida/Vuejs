<template>
  <div class="new-task">
      <input type="text" v-model="texto" @keypress.enter="add" class="form-element" placeholder="Digite uma tarefa">
      <button class="btn btn-primary form-element" @click="add" >+</button>
      
  </div>
</template>

<script>
export default {
   
    data() {
        return {
            texto : ""
        }
    },
    methods:{
        add(){
            this.$emit("TaskAdd",{name: this.texto})
            this.texto = ""
        }
    }
}
</script>

<style>
    .new-task{
        display: flex;
        margin: 35px;
    }
    .form-element{
        outline: none;
        font-size: 2rem;
        border:1px solid #FFF;
        padding: 5px 10px 8px;
        color: #FFF;
    }
    input.form-element{
        width: 500px;
        background-color: #FFF2;
        border-top-left-radius: 8px;
        border-bottom-left-radius: 8px;
    }
    button.form-element{
        border-top-right-radius: 8px;
        border-bottom-right-radius: 8px;
        border-left: none;
    }
</style>