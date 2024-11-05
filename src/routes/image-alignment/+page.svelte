<script>
	
	import defaultImage from '$lib/images/samples/ad-astra.jpg';

	const variationMin = 500;
	const sampleWidth = 32;
	const sampleHeight = 18;
	const sampleImageModules = import.meta.glob(
		'/src/lib/images/samples/*.jpg',
		{eager: true}
	);
	
	/* State */
	let selectedImage = $state();
	let alignment = $derived(selectedImage ? getBestAlignment(selectedImage) : null);

	/* Component mounting */
	$effect(() => {
		const img = new Image();
		img.src = defaultImage;
		selectedImage = img;

	});

	/* Utils */
	const rgbToHsl = (r, g, b) => {
		r /= 255;
		g /= 255;
		b /= 255;
		const l = Math.max(r, g, b);
		const s = l - Math.min(r, g, b);
		const h = s ? (l === r ? (g - b) / s : l === g ? 2 + (b - r) / s : 4 + (r - g) / s) : 0;
		return [
			60 * h < 0 ? 60 * h + 360 : 60 * h,
			100 * (s ? (l <= 0.5 ? s / (2 * l - s) : s / (2 - (2 * l - s))) : 0),
			(100 * (2 * l - s)) / 2
		];
	};

	const getLightnessVariation = (imageData) => {
		let variation = 0;
		let lastL;
		for (var i = 0; i < imageData.length; i += 4) {
			const hsl = rgbToHsl(imageData[i], imageData[i + 1], imageData[i + 2]);
			const l = hsl[2];
			variation += Math.abs(l - (lastL || l));
			lastL = l;
		}
		return variation;
	};

	const getBestAlignment = (image) => {
		if (!image) return;
		var canvas = document.createElement('canvas');
		canvas.width = 32;
		canvas.height = 18;
		var ctx = canvas.getContext('2d', { willReadFrequently: true });
		ctx.drawImage(image, 0, 0, sampleWidth, sampleHeight);

		const tlImageData = ctx.getImageData(0, 0, sampleWidth/2, sampleHeight/2).data;
		const blImageData = ctx.getImageData(0, sampleHeight/2, sampleWidth/2, sampleHeight/2).data;
		const trImageData = ctx.getImageData(sampleWidth/2, 0, sampleWidth/2, sampleHeight/2).data;
		const brImageData = ctx.getImageData(sampleWidth/2, sampleHeight/2, sampleWidth/2, sampleHeight/2).data;

		const quadrants = [
			{
				name: 'top left',
				imageData: tlImageData,
				variation: getLightnessVariation(tlImageData)
			},
			{
				name: 'bottom left',
				imageData: blImageData,
				variation: getLightnessVariation(blImageData)
			},
			{
				name: 'top right',
				imageData: trImageData,
				variation: getLightnessVariation(trImageData)
			},
			{
				name: 'bottom right',
				imageData: brImageData,
				variation: getLightnessVariation(brImageData)
			}
		];

		quadrants.sort((a, b) => b.variation - a.variation);
		quadrants.map((q) => {
			console.log(`${q.name} : ${q.variation}`);
		});

		// TODO: We should actually look at thresholds across values to determine center center or other value
		// but just looking to see if there is little variation in the lowest will do for now
		return quadrants[3].variation > variationMin ? 'center center' : quadrants[0].name;
	};

	/* Event handlers */
	const onImageInputChange = (e) => {
		const imageFile = e.target?.files?.[0];

		if (!imageFile) return;
		const reader = new FileReader();
		reader.onload = function (e) {
			const img = new Image();
			img.src = e.target.result;
			selectedImage = img;
		};
		reader.readAsDataURL(imageFile);
	};

	const onSampleSelect = (e) => {
		selectedImage = e.target;
	};
</script>

<svelte:head>
	<title>Image Alignment Sample</title>
	<meta name="description" content="Samples and image and decides the best alignment" />
</svelte:head>

<div class="text-column">
	<h1>Image Auto-Alignment</h1>
	<p>
		An simple example of analyzing and image and aligning it to the most interesting area within
		that image. This is done by breaking the pixels into quadrants and looking at the overall
		difference between lightness values for each quadrant. The highest variation quadrant wins.
		There are some thresholds to also align center if the overall image varies enough.
	</p>

	<div class="instructions">
		<p>Select a sample below or browse for your own test image</p>
		<input type="file" class="image-input" accept="image/*" onchange={onImageInputChange} />
	</div>

	<div class="samples">
		{#each Object.entries(sampleImageModules) as [_path, module]}
			<img src={module.default} alt="some alt text" onclick={onSampleSelect} />
		{/each}
	</div>

	<div class="preview-area">
		<img
			class="preview"
			alt="Preview"
			src={selectedImage ? selectedImage.src : null}
			style="object-position: {alignment};"
		/>
		<h5>Aligned: {alignment}</h5>
	</div>
</div>

<style>
	.instructions {
		text-align: center;
	}

	.image-input {
		background-color: #808080;
		color: white;
		border-radius: 4px;
		border: 1px solid white;
	}

	.samples {
		display: flex;
		gap: 16px;
		padding: 16px;
		flex-flow: row wrap;
		justify-content: center;
	}

	.samples img {
		width: 128px;
		height: auto;
		border-radius: 8px;
		display: block;
		transition: transform 0.2s;
	}

	.samples img:hover {
		outline: 2px solid orange;
		transform: scale(1.1);
		cursor: pointer;
	}

	.preview-area {
		display: flex;
		flex-flow: column nowrap;
		align-items: center;
		padding: 32px;
	}

	.preview {
		border-radius: 8px;
		box-shadow: 8px 8px 8px rgba(0,0,0,.2);
		width: 400px;
		height: 400px;
		object-fit: cover;
		transition: object-position 0.3s ease-in-out;
	}
</style>
