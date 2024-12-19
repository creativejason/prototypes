<script>
	let {url} = $props();

</script>

<div class="artwork"></div>

<style lang="less">
    .artwork{
		/*--height:calc(100vw/2*3);*/
		width: 100vw;
		height: 100vw;
		background-image: url('/images/responsive-details/poster.jpg');
		mask-image: linear-gradient(to bottom, rgba(0,0,0,1), rgba(0,0,0,0));
		mask-size: 100% 100%;
		background-size: 100% auto;
		background-position: top center;
		background-repeat: no-repeat;
		transition: background-image 500ms ease-in-out;
	}

    @media (min-width: 600px), (height <= 700px) {
        .artwork{
            height: calc(100vw/16*9);
            background-image: url('/images/responsive-details/background.jpg');
            mask-image: linear-gradient(to bottom, rgba(0,0,0,1), rgba(0,0,0,0));
        }
    }

	@media (min-width: 1100px) {

		.artwork{
			position: absolute;
			top:0;
			right:0;
			width: 75vw;
			max-width: 1600px;
			height: calc(75vw/16*9);
			max-height: 900px;
			mask-size: 100% 100%;
			mask: linear-gradient(to bottom, rgba(0,0,0,1) 50%, rgba(0,0,0,0)), linear-gradient(to left, rgba(0,0,0,0) 50%, rgba(0,0,0,1));
			mask-composite: subtract; /*5*/
		}
	}

</style>