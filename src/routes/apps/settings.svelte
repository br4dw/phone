<style>
	.app-container {
		padding: 10px;
		background-color: rgba(42, 44, 53, 0.7);
    	color: white;
	}
</style>

<script>
    import TopIcons from '../../components/TopIcons.svelte';
	import BottomIcons from '../../components/BottomIcons.svelte';
    import SettingsApp from "../../components/apps/SettingsApp.svelte";
</script>

<svelte:head>
	<title>Settings</title>
</svelte:head>

<div class="phone">
    <TopIcons />
	<div class="app-container">
		<SettingsApp />
	</div>
	<BottomIcons />
</div>