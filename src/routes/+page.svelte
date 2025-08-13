<script lang="ts">
	import { Button, Input } from 'flowbite-svelte';

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

<div class="mt-15 h-full w-full justify-items-center">
	<h1 class="m-5 text-5xl text-white drop-shadow-lg">To-do list</h1>

	<form on:submit={handleSubmit}>
		<div class="flex w-100 flex-row">
			<Input type="text" bind:value={inputValue} />
			<Button class="ms-3" type="submit" color="blue">Add</Button>
		</div>
	</form>

	{#each todos as todo}
		<div
			class="m-3 flex w-100 flex-row items-center rounded-lg border border-gray-300 bg-gray-50 p-3 text-gray-900 drop-shadow-md dark:border-gray-600 dark:bg-gray-700 dark:text-white"
		>
			<div class="break-word w-90">
				{todo.todoText}
			</div>
			<Button class="h-10 w-10" color="red" onclick={() => handleDelete(todo.Id)}>X</Button>
		</div>
	{/each}

	{#if todos.length == 0}
		<div class="mt-15">
			<img src="/img/doodle1.png" alt="Lady sitting at couch" />
		</div>
	{/if}
</div>
