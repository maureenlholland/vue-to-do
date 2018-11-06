<template>
	<div class="todo__list">
		<p v-if="todos.length === 0">Nothing to do!</p>
		<ul class="list" v-else>
			<li v-for="(todo, i) in todos" :key="i">
					<div v-if="todo.update">
						<input type="text" v-model="updateText" :placeholder="todo.todo">
						<span>
							<button class="action" @click="updateToDo(i, updateText)">Confirm</button>
							<button class="warning" @click="todo.update = false">Cancel</button>
						</span>
					</div>
					<div v-else>
						{{todo.todo}}
						<span>
							<button class="action" @click="showInput(todo)">Edit</button>
							<button class="warning" @click="deleteToDo(i)">Delete</button>
						</span>
					</div>
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