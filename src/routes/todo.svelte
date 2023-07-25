<script context="module">
	import { browser, dev } from '$app/env';

	// we don't need any JS on this page, though we'll load
	// it in dev so that we get hot module replacement...
	export const hydrate = dev;

	// ...but if the client-side router is already loaded
	// (i.e. we came here from elsewhere in the app), use it
	export const router = browser;

	export const prerender = true;
</script>

<script>
	import { v4 as uuid } from 'uuid';
	import { slide } from 'svelte/transition';
	import { onMount } from 'svelte';

	let todos = [];
	let todoText = '';

	onMount(() => {
		const existingTodos = localStorage.getItem('todos');
		todos = JSON.parse(existingTodos) || [];
	});

	const addTodo = () => {
		todos = [
			...todos,
			{
				id: uuid(),
				text: todoText,
				complete: false
			}
		];
		localStorage.setItem('todos', JSON.stringify(todos));
		todoText = '';
	};

	const deleteTodo = (idToDelete) => {
		todos = todos.filter((todo) => todo.id != idToDelete);
		localStorage.setItem('todos', JSON.stringify(todos));
	};
</script>

<svelte:head>
	<title>Todo - Svelte</title>
</svelte:head>

<main>
	<div>
		<h1>Todo</h1>
		<div>
			{#each todos as todo}
				<div class="todo-item" transition:slide|local>
					<input type="checkbox" bind:checked={todo.complete} />
					<span class={todo.complete ? 'text completed' : 'text'}>{todo.text}</span>
					<button on:click={deleteTodo(todo.id)}>X</button>
				</div>
			{/each}
		</div>
		<form on:submit|preventDefault={addTodo} class="new-todo">
			<input type="text" bind:value={todoText} placeholder="New todo" />
			<button type="submit">Save</button>
		</form>
	</div>
</main>
<footer>
	<a href="/pager">Previous Page</a>
	<a href="/languages">Next Page</a>
</footer>

<style>
	main {
		font-family: sans-serif;
		text-align: center;
		width: 80%;
		margin: auto;
	}

	.todo-item {
		border-top: 1px solid lightgray;
		padding: 0.5rem 0;
	}

	.text {
		margin: 0 0.5rem;
	}

	.completed {
		text-decoration: line-through;
		color: gray;
	}

	.new-todo {
		margin: 1rem;
	}

	footer {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
</style>
