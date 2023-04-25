<script lang="ts">

	// Imports:
	import Nav from '$lib/Nav.svelte';
	import Footer from '$lib/Footer.svelte';
	import '../app.css';
	import user from '../user'
	
	$: isLoggedIn = $user === null ? false : true;
</script>

<!-- #################################################################################################### -->

<!-- Navbar -->
{#if isLoggedIn}
<Nav />
{:else}
<!Nav/>
{/if}

<!-- App Content -->
<main><slot /></main>

<!-- Footer -->
<Footer />

<!-- #################################################################################################### -->

<style>

	main {
		padding-top: 3em;
		padding-left: 1em
	}

</style>