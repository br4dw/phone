<script>
	export let status;
	export let error;

	const dev = process.env.NODE_ENV === 'development';
</script>

<style>
	.centered {
		text-align: center;
		vertical-align: middle;
		align-items: center;
	}
	.spacer-top {
		margin-top: 100px;
	}
</style>

<svelte:head>
	<title>🍃 White Widow 🍃 - {status} ({error.message})</title>
</svelte:head>

<br /><br />
<div class="centered">
	<h1 class="spacer-top">{status}</h1>
</div>

{#if dev && error.stack}
	<p class="centered">{error.message}</p>
	<pre >
		{error.stack}
	</pre>
{:else if !error.stack}
	<h2 class="centered">{error.message}</h2>
{/if}
<br />