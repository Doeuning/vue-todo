<template>
	<div id="app">
		<TodoHeader></TodoHeader>
		<TodoInput v-on:addTodo="addTodo"></TodoInput>
		<TodoList v-bind:propsdata="todoItems"></TodoList>
		<TodoFooter v-on:removeAllTrg="removeAll"></TodoFooter>
	</div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
	data() {
		return {
			todoItems: []
		}
	},
	created(){
		if(localStorage.length > 0) {
			for (var i = 0; i < localStorage.length; i++){
				this.todoItems.push(localStorage.key(i))
			}
		}
	},
	methods: {
		addTodo(item){
			localStorage.setItem(item, item);
			this.todoItems.push(item);
		},
		removeAll(){
			localStorage.clear();
			this.todoItems = [];
		}
	},
	components: {
		'TodoHeader': TodoHeader,
		'TodoInput': TodoInput,
		'TodoList': TodoList,
		'TodoFooter': TodoFooter
	}
}
</script>

<style>
    body {
		background: #e1e1e1;
		text-align: center;
	}
	#app {
		max-width: 500px;
		margin: 0 auto;
	}
	input {
		border-style: groove;
		box-sizing: border-box;
		padding: 0 20px;
	}
	button {
		border-style: groove;
	}
	.shadow {
		box-shadow: 5px 10px 10px rgba(0, 0, 0, .03);
    }
</style>
