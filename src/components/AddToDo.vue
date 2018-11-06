<template>
	<div>
		<form>
			<label for="new">Add to-do
				<input id="new" type="text" v-model="newToDo" required>
			</label>
			<input type="submit" value="Add to List" @click.prevent="addToDo">
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
			// showToDo(){
			// 	console.log(this.newToDo);
			// 	this.$emit('showNew', this.newToDo);
			// },
			// submit button inactive until text is in new field
			addToDo(){
				if (this.newToDo) {
					this.$emit('addNew', this.newToDo);
					this.newToDo = '';
				} 
			}
		}
	}
</script>