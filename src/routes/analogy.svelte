<script>
	let god = '';
	let man = '';
	let inSync = false;
</script>

<svelte:head>
	<title>Analogy</title>
</svelte:head>

<main>
	<h1>Analogy</h1>
	<div class="radio-group">
		<label class="red-text">
			<input type="radio" bind:group={inSync} value={false} />
			Out-of-Sync
			{#if !inSync}
				❌
			{/if}
		</label>
		<label class="green-text">
			<input type="radio" bind:group={inSync} value={true} />
			In-Sync
			{#if inSync}
				✅
			{/if}
		</label>
	</div>
	<div class="text-inputs">
		<div>
			<label for="god">God</label>
			<input type="text" id="god" bind:value={god} />
		</div>
		<div>
			<label for="man">Man</label>
			{#if !inSync}
				<input type="text" id="man" bind:value={man} />
			{:else}
				<input type="text" id="man" bind:value={god} />
			{/if}
		</div>
	</div>
</main>

<footer>
	<a href="/languages">Previous Page</a>
</footer>

<style>
	.radio-group {
		margin: 2rem 0;
	}

	.text-inputs div {
		margin: 1rem 0;
	}

	label {
		font-weight: bold;
		font-size: large;
	}

	.green-text {
		color: green;
	}

	.red-text {
		color: red;
	}
</style>
