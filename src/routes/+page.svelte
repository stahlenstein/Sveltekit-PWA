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
<h1> </h1>
{#if isLoggedIn}
<nav />
<h2> {$user.firstname} has logged out.</h2>
<input type="button" value="Logout!" on:click={logout}/>
{:else}
<h2> </h2>
<Login />
{/if}
</div>

<style>
div {
  position: relative;
  display: flex;
  background-color: rgb(106, 106, 106);
  align-items: center;
  height:400px;
  width:300px;

}
</style>