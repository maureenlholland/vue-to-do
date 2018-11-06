<template>
	<div>
		<form>
			<label for="new">Add to-do
				<input id="new" type="text" v-model="newToDo" required>
			</label>
			<input class="action" type="submit" value="Add to List" @click.prevent="addToDo">
		</form>
	</div>
</template>

<script>
	export default {
		name: 'AddToDo',
		data: () => {
			return {
				newToDo: ''
			}
		},
		props: ['todos'],
		methods: {
			addToDo(){
				if (this.newToDo) {
					this.$emit('addNew', this.newToDo);
					this.newToDo = '';
				} 
			}
		}
	}
</script>