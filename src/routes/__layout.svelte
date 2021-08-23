<script>
	import Navbar from '$lib/Navbar.svelte';
	import '../app.css';
</script>

<body>
	<Navbar />
	<main>
		<slot />
	</main>
</body>

<style>
	main {
		margin: 4rem;
	}
</style>
