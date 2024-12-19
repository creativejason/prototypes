<script>
	let { children } = $props();
</script>

<div class="device-container">
    {@render children()}
</div>

<style lang="less">
    .device-container{
		width:100vw;
		min-height: 100vh;
		display: flex;
		flex-flow: column nowrap;
		background-color: black;
		color: rgba(255, 255, 255, 0.80);
		font-family: "Inter", serif;
		font-optical-sizing: auto;
		font-weight: 400;
		font-style: normal;
		font-size:small;
	}
</style>