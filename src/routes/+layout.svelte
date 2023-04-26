<script lang="ts">
  // Imports:
  import Nav from "$lib/Nav.svelte";
  import Footer from "$lib/Footer.svelte";
  import "../app.css";
  import user from "../user";
  import { redirect } from "@sveltejs/kit";

  $: isLoggedIn = $user === null ? false : true;
</script>

<!-- #################################################################################################### -->

<!-- Navbar -->
{#if isLoggedIn}
  <Nav />
{:else}
  <!Nav />
{/if}

<!-- App Content -->
<main class="main">
  <div class="loginBox">
    <slot />
  </div>
</main>

<!-- Footer -->
<Footer />

<!-- #################################################################################################### -->

<style>
	.main {
		width: 100%;
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
	}

  .loginBox {
    display: flex;
    width: 20rem;
    height: 25rem;
    background-color: white;
    padding: 1em;
    border-radius: 0.3rem;
		align-items: center;
		justify-content: center;
  }
</style>
