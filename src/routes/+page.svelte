<script>
  import user from '../user';
  import Login from '../lib/Login.svelte';
  import { USER } from '$env/static/private';

  $: isLoggedIn = $user === null ? false : true;

  const logout = () => {
    user.update(val => val = null)
  }
</script>

<div>

{#if isLoggedIn}
<nav />
<h2> {$user.firstname} has logged out.</h2>
<input type="button" value="Logout!" on:click={logout}/>
{:else}

<Login />
{/if}
</div>

<style>

</style>