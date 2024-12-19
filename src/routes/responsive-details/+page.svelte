<script>
	
	import TitleArt from '../../lib/components/TitleArt.svelte';
	import Actions from '../../lib/components/Actions.svelte';
	import { extractColors } from "extract-colors";
	import SocialProof from '../../lib/components/SocialProof.svelte';
	import Summary from '../../lib/components/Summary.svelte';
	import StatusBar from '../../lib/components/StatusBar.svelte';
	import BackgroundArt from '../../lib/components/BackgroundArt.svelte';
	import ModalButtonBar from '../../lib/components/ModalButtonBar.svelte';
	import DeviceContainer from '../../lib/components/DeviceContainer.svelte';
	import AppContainer from '../../lib/components/AppContainer.svelte';
	import Metadata from '../../lib/components/Metadata.svelte';
	
	let ultrablur = $state({
		tl: "#000",
		tr: "#000",
		bl: "#000",
		br: "#000"
	});

	$effect(() => {
		extractColors("images/responsive-details/poster.jpg").then((palette) => {
			console.log(palette);
			palette.sort((a, b) => a.lightness - b.lightness);
			ultrablur = {
				tl: palette[0].hex + "40",
				tr: palette[1].hex + "40",
				br: palette[2].hex + "40",
				bl: palette[3].hex + "40",
			}	
		}).catch(console.error);
	});

</script>

<svelte:head>
	<title>Details Responsive Example</title>
	<meta name="description" content="Prototype of responsive detail page" />
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap" rel="stylesheet">
</svelte:head>

<DeviceContainer>
	<StatusBar />
	<AppContainer ultrablur={ultrablur}>
		<ModalButtonBar />
		<BackgroundArt />
		<div class="content">
			<TitleArt url="images/responsive-details/clear-logo.png" title="Wicked" />
			<Metadata />
			<Actions />
			<Summary />
			<SocialProof />			
		</div>
	</AppContainer>
</DeviceContainer>
<style>

	.content{
		margin-top:-128px;
		display: flex;
		flex-flow: column nowrap;
		align-items: inherit;
		gap:32px;
		padding: 0 24px;
		position: relative;
		max-width: 800px;
		display: flex;
		flex-flow: column nowrap;
	}

	@media (min-width: 1100px) {

		.content{
			margin-top: 128px;
			width: 50vw;
			align-items: inherit;
			padding: 0 48px;
			font-size: medium;
		}
	}


</style>
