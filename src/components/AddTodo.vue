<!-- unused -->
<template>
	<div>
		<form @submit="addTodo">
			<input type="text" v-model="title" name="title" placeholder="add todo...">
			<input type="submit" value="Submit" class="btn">
		</form>
	</div>
</template>

<script>
	export default {
		name: "AddTodo",
		data() {
			return {
				title: ""
			}
		},
		methods: {
			addTodo(e){
				e.preventDefault();
				const newTodo = {
					title: this.title,
					completed: false
				}

				//Send upto the parent
				this.$emit('add-todo', newTodo);
				this.title = '';			
			}
		}
	}
</script>

<style scoped>
form {
	display: block;
}
form input {
	display: inherit;
	margin: auto;
}
input[type="text"] {
	padding: 5px;
}
input[type="submit"] {
}
</style>