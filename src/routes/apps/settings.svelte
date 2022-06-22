<style>

	*, *::before, *::after {
		box-sizing: border-box;
	}

	:root {
		--phone-width: 20em; /* dont go below 20 or above 60 xd */
		--border-size: .2em;
		--app-size: calc((var(--phone-width) / 8) + .5em);
		--phone-height: calc(var(--phone-width) * 2);
		--border-radius: 35px;
		--border-color: white;
		--notch-height: calc(var(--phone-width) / 10 / 2);
		--app-bg: #FFFA;
		--bottom-bg: rgba(0, 0, 0, 0.3);
		--top-bg: rgba(0, 0, 0, 0.8);
		--app-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
	}

	.phone {
		display: grid;
		grid-template-columns: repeat(1, 1fr);
		grid-template-rows: repeat(15, 1fr);
		width: var(--phone-width);
		height: var(--phone-height);
		min-width: 20em;
		min-height: 40em;
		border: var(--border-size) solid var(--border-color);
		background-color: transparent;
		background-image: url("https://source.unsplash.com/kMxlbbzbFhQ");
		background-position: center;
		background-repeat: no-repeat;
		background-size: var(--phone-width) var(--phone-height);
		border-radius: var(--border-radius);
		margin: 0 auto;
	}
	.phone:last-child {
		grid-row-start: 7;
	}
</style>

<script>
    import TopIcons from '../../components/TopIcons.svelte';
	import BottomIcons from '../../components/BottomIcons.svelte';
    import SettingsApp from "../../components/apps/Settings.svelte";
</script>

<svelte:head>
	<title>Settings</title>
</svelte:head>


<div class="phone">
	<TopIcons />
	<SettingsApp />
	<BottomIcons />
</div>