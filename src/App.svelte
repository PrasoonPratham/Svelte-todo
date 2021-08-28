<script>
	let todos = [];
	let todo = '';
	let num = 0;
	function addTodo() {
		if (todo) {
			todos = [
				... todos,
				{
					text: todo,
					id: num
				}
			]
		}
		todo = '';
		num++;
		console.log(todos)
	}
	function removeTodo(id) {
		const number = todos.findIndex(todo => todo.id === id);
  		todos.splice(number, 1);
 		todos = todos;
	}
</script>

<main>

	<form on:submit|preventDefault="{addTodo}">
		<input type="text" placeholder="Add a todo" bind:value={todo}/>
		<button type="submit">
			Submit
		</button>
	</form>

	<ul>
		{#each todos as item}
			<li>
				{item.text}
				<button on:click={()=> removeTodo(todo.id)}>
				</button>
			</li>
		{/each}
	</ul>

</main>

<style>
main{
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	padding-top: 2em;
}
</style>