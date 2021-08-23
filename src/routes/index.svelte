<script context="module">
	// since there's no dynamic data here, we can prerender
	// it so that it gets served as a static asset in prod
	export const prerender = true;
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<main>
	<h1>Welcome Home</h1>
</main>
<footer>
	<a href="/pager">Next Page</a>
</footer>

<style>
	footer a {
		display: block;
		text-align: right;
	}
</style>
