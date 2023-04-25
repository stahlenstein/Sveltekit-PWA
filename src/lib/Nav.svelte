<script lang="ts">

	// Initializations:
	const links = [
		{ route: '/', name: 'Home' },
		{ route: '/about', name: 'About' }
	];

</script>

<!-- #################################################################################################### -->

<nav>

	<!-- Navigation Links -->
		<button>
		<svg
			xmlns="http://www.w3.org/2000/svg" 
			height="32" 
			viewBox="0 96 960 960" 
			width="32">
			<path 
			d="M150 822.696q-14.424 0-24.245-9.871-9.82-9.871-9.82-24.37 0-14.498 9.82-24.194 9.821-9.696 24.245-9.696h660q14.424 0 24.245 9.871 9.82 9.871 9.82 24.37 0 14.498-9.82 24.194-9.821 9.696-24.245 9.696H150Zm0-212.631q-14.424 0-24.245-9.871-9.82-9.871-9.82-24.369 0-14.499 9.82-24.195 9.821-9.695 24.245-9.695h660q14.424 0 24.245 9.871 9.82 9.871 9.82 24.369 0 14.499-9.82 24.195-9.821 9.695-24.245 9.695H150Zm0-212.63q-14.424 0-24.245-9.871-9.82-9.871-9.82-24.37 0-14.498 9.82-24.314 9.821-9.815 24.245-9.815h660q14.424 0 24.245 9.991 9.82 9.99 9.82 24.489 0 14.498-9.82 24.194-9.821 9.696-24.245 9.696H150Z"/>
		</svg>
	</button>

	<ul class="links">
		{#each links as link}
			<li><a href="{link.route}">{link.name}</a></li>
		{/each}
	</ul>

</nav>

<!-- #################################################################################################### -->

<style>

	nav {
		display: flex;
		position: relative;
		align-items: center;
		height: 53px;
		width: auto;
		padding: 0 24px;
		top: 15px;
		margin-right: 10px;
		margin-left: 10px;
		margin-bottom: 20px;
		border-radius: .5rem;
		background-color: rgba(0, 0, 0, 0.25);
		backdrop-filter: blur(50px);
		border-bottom: 2px solid rgba(34,40,49,0.3);
		box-shadow: 0px -5px 100px rgba(0, 0, 0, 0.417);
	}

	button {
		background-color: transparent;
		border: none;
		fill: white;	
	}

	.links {
		display: flex;
	}
	
	.links li {
		margin: 0 1em 0 1em;
		list-style: none;
	}

	.links a {
		color: inherit;
		text-decoration: none;
	}

	button:hover {
		border-radius: 3px;
		background-color: var(--secondary-color);
		transition-duration: ease-out 1s;
		transition-delay: 0s;
	}
	
</style>