<template>
	<div id="app">
		<h1>Tarefas</h1>
		
		<BarraTarefas :tasks="tasks"/>
		<NewTask  @TaskAdd="addTask"/>
		<Tasks :tasks="tasks" @taskDelete="deleteTask" 
			@toggleTask="toggleTask"/>
		
	</div>
</template>

<script>
import Tasks  from './components/TaskGrid.vue';
import NewTask from './components/NewTask.vue';
import BarraTarefas from './components/BarraTarefas.vue';
export default {
	
	components:{Tasks, NewTask, BarraTarefas},
	data() {
		return {
			tasks : []
		}
	},
	watch:{
		tasks:{
			deep:true,
			handler(){
				localStorage.setItem("tasks", JSON.stringify(this.tasks))
			} 
		}
	},
	methods:{
		addTask(task){
			const sameName = element => element.name === task.name
			const reallyNew = this.tasks.filter(sameName).length === 0
			
			if(reallyNew){
				this.tasks.push({name:task.name, pending:task.pending || true})
				
			}
		},
		deleteTask(event){
			this.tasks.splice(event,1)
			
		},
		toggleTask(i){
			this.tasks[i].pending = !this.tasks[i].pending
		}
	},
	created(){
		const json = localStorage.getItem("tasks")
		this.tasks = JSON.parse(json) || []
	}
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 10px;
		font-weight: 600;
		font-size: 3rem;
		font-family: sans-serif;
		color: rgba(198, 198, 252, 0.904);
	}
</style>
