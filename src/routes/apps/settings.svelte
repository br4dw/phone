<style>

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
	<div class="app-container">
		<SettingsApp />
	</div>
	<BottomIcons />
</div>