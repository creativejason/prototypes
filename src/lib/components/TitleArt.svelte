<script>
	let {url, title} = $props();
</script>

<div class="logo" style="background-image:url({url})" title="{title}"></div>

<style lang="less">
    .logo{
		aspect-ratio: 4 / 1;
		width: 100%;
		max-width: 600px;
		min-width: 280px;
		background-repeat: no-repeat;
		background-position: bottom center;
		background-size: contain;
	}

	@media (min-width: 1100px) {
		.logo{
				background-position: bottom left;
		}
	}
</style>