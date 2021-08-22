<script>
	import { page } from '$app/stores';
</script>

<svelte:head>
	<title>Language - {$page.params.name}</title>
</svelte:head>

<h3>
	Here's the language: {$page.params.name}
</h3>

<a href="/languages">Go back to Languages</a>
