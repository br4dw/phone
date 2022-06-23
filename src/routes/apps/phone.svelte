<style>

</style>

<script>
    import TopIcons from '../../components/TopIcons.svelte';
	import BottomIcons from '../../components/BottomIcons.svelte';
    import PhoneApp from "../../components/apps/PhoneApp.svelte";
</script>

<svelte:head>
	<title>Phone</title>
</svelte:head>

<div class="phone">
    <TopIcons />
	<div class="app-container">
		<PhoneApp />
	</div>
	<BottomIcons />
</div>