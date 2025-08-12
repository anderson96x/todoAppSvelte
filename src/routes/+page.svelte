<script lang="ts">
	let todos: any = [];

	let inputValue = '';
	const handleSubmit = () => {
		todos = [...todos];
		todos.push({ todoText: inputValue, Id: crypto.randomUUID() });
		inputValue = '';
		console.log(todos);
	};

	const handleDelete = (id: string) => {
		todos = todos.filter((item: any) => item.Id !== id);
	};
</script>

<form on:submit={handleSubmit}>
	<input type="text" bind:value={inputValue} />
	<button>Add</button>
</form>

{#each todos as todo}
	<div class="flex flex-row">
		<div>{todo.todoText}</div>
		<button on:click={() => handleDelete(todo.Id)}>X</button>
	</div>
{/each}
