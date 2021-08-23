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
	body {
		padding: 2rem;
	}

	@media only screen and (max-width: 600px) {
		body {
			padding: 0.5rem;
		}
	}

	main {
		margin: 4rem;
	}
</style>
