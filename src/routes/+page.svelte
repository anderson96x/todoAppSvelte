<script lang="ts">
	let todos: any = [];

	let inputValue = '';
	let handleSubmit = () => {
		todos = [...todos];
		todos.push({todoText: inputValue, Id: crypto.randomUUID()});
        console.log(todos);
	};
</script>

<form on:submit={handleSubmit}>
	<input type="text" bind:value={inputValue} />
	<button>Add</button>
</form>

{#each todos as todo}
	<p>{todo.todoText}</p>
{/each}
