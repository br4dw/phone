<style>

</style>

<script>
    import TopIcons from '../../components/TopIcons.svelte';
	import BottomIcons from '../../components/BottomIcons.svelte';
    import CalculatorApp from "../../components/apps/Calculator.svelte";
</script>

<svelte:head>
	<title>Calculator</title>
</svelte:head>

<div class="phone">
    <TopIcons />
	<div class="app-container">
		<CalculatorApp />
	</div>
	<BottomIcons />
</div>