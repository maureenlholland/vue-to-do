<template>
	<div>
		<p v-if="todos.length === 0">Nothing to do!</p>
		<ul class="list" v-else>
			<li v-for="(todo, i) in todos" :key="i">
					<span v-if="todo.update">
						<input type="text" v-model="updateText" :placeholder="todo.todo">
						<button @click="updateToDo(i, updateText)">Confirm</button>
						<button @click="todo.update = false">Cancel</button>
					</span>
					<span v-else>
						{{todo.todo}}
						<button @click="showInput(todo)">Edit</button>
						<button @click="deleteToDo(i)">Delete</button>
					</span>
			</li>
		</ul>
	</div>
</template>

<script>

	export default {
		name: 'ToDoList',
		props: ['todos'],
		data: () => {
			return {
				updateText: ''
			}
		},
		methods: {
			deleteToDo(i){
				this.$emit('toDoDeleted', i)
			},
			updateToDo(i, newTodo){
				this.$emit('toDoUpdated', i, {todo: newTodo, update: false});
				this.updateText = '';
			},
			showInput(todo){
				todo.update = true;
			}
		}
	}
</script>