<script lang="ts">
	import { Pen } from '@lucide/svelte';

	let mouseHoverTodoName: boolean = false;
	let todoName: string = 'To-do list';
</script>

<div
	class="my-5 flex w-[35rem] flex-row-reverse {mouseHoverTodoName
		? 'border-1 border-[#94c5cc]'
		: 'border-1 border-black'}"
	role="region"
	aria-label="To-do list title"
	on:mouseover={() => (mouseHoverTodoName = true)}
	on:focus={() => (mouseHoverTodoName = true)}
	on:mouseleave={() => (mouseHoverTodoName = false)}
	on:blur={() => (mouseHoverTodoName = false)}
>
	<div class="flex justify-center m-0 p-0">
		<Pen color="white" size="1rem"/>
	</div>
	<div class="w-[35rem]">
		<input
			type="text"
			maxlength="18"
			class="m-0 p-0 h-[5rem] w-[35rem] border-0 bg-transparent text-center text-5xl text-white ring-transparent break-words"
			bind:value={todoName}
		/>
	</div>
</div>
