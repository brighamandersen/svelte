<nav>
	<ul>
		<li><a href="/"><h1>Svelter</h1></a></li>
		<li><a href="/pager">Pager</a></li>
		<li><a href="/todo">Todo</a></li>
		<li><a href="/languages">Languages</a></li>
		<li><a href="/analogy">Analogy</a></li>
	</ul>
</nav>

<style>
	nav {
		margin: 2rem;
	}

	h1 {
		font-size: 60px;
		font-weight: bold;
		margin: 0.5rem;
	}

	ul {
		display: flex;
		align-items: center;
		justify-content: space-around;
		padding: 0;
	}
	@media only screen and (max-width: 600px) {
		ul {
			flex-direction: column;
		}
	}

	li {
		list-style-type: none;
		font-size: large;
	}
</style>
