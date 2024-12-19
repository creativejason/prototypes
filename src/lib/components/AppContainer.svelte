<script>
	let { children, ultrablur } = $props();
</script>

<div class="app-container" style="--ub-tl:{ultrablur.tl}; --ub-tr:{ultrablur.tr}; --ub-bl:{ultrablur.bl}; --ub-br:{ultrablur.br};">
    {@render children()}
</div>

<style lang="less">
    .app-container{
		background-color: black;
		color: rgba(255, 255, 255, 0.80);
		font-family: "Inter", serif;
		font-optical-sizing: auto;
		font-weight: 400;
		font-style: normal;
		font-size:small;
		flex: 1;
		display: flex;
		flex-flow: column nowrap;
		align-items: center;
		border-radius: 24px 24px 0 0;
		overflow: hidden;
		position: relative;
		background-image:   
			radial-gradient(circle farthest-side at top left, var(--ub-tl) 0, transparent 60%),
			radial-gradient(circle farthest-side at top right, var(--ub-tr) 0, transparent 60%),
			radial-gradient(circle farthest-side at bottom right, var(--ub-br) 0, transparent 60%),
			radial-gradient(circle farthest-side at bottom left, var(--ub-bl) 0, transparent 60%);
	}

	@media (min-width: 1100px) {
       
	   .app-container{
		   align-items: start;
	   }
   }
</style>