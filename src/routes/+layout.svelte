<script>
    import { connected } from '$lib/stores/session.svelte.js';
	let { children } = $props();
</script>

<h1> Online games (header) </h1>

<nav>
    {#if $connected}
        <a href="/dashboard"> Dashboard </a>
        <a href="/games"> Games </a>
    {:else}
        <a href="/"> Homepage </a>
        <a href="/signup"> Sign up </a>
        <a href="/login"> Log in </a>
    {/if}
</nav>

{@render children()}
