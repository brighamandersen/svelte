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
	import Page1 from '$lib/Page1.svelte';
	import Page2 from '$lib/Page2.svelte';

	let currentPage = 1;

	function changePage(newPage) {
		currentPage = newPage;
	}
</script>

<svelte:head>
	<title>Pager - Svelter</title>
</svelte:head>

<h1>Choose a page</h1>
<div class="page-nav">
	<button on:click={() => changePage(1)} class={currentPage == 1 && 'active'}> Page 1 </button>
	<button on:click={() => changePage(2)} class={currentPage == 2 && 'active'}> Page 2 </button>
	<input type="text" placeholder="Enter pg number" bind:value={currentPage} />
</div>
<div class="page-container">
	{#if currentPage == 1}
		<Page1 {changePage} />
	{:else if currentPage == 2}
		<Page2 {changePage} />
	{:else}
		<p>Enter a page number between 1-2</p>
	{/if}
</div>
<footer>
	<a href="/">Previous Page</a>
	<a href="/todo">Next Page</a>
</footer>

<style>
	.page-container {
		width: 100%;
		height: 50vh;
		background: rgb(241, 241, 241);
		border: 1px solid black;
	}

	.active {
		border: 1px solid black;
		border-bottom: 4px solid black;
	}

	footer {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
</style>
