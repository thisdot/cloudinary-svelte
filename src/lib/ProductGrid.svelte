<script>
	import { CldImage } from 'svelte-cloudinary';

	/**
	 * @type {{ src: string, title: string, effects?: Array<unknown>, overlays?: Array<unknown> }[]}
	 */
	export let images = [];
</script>

<div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 p-4">
	{#each images as image}
		<div class="overflow-hidden rounded-lg">
			<CldImage
				width={500}
				height={500}
				crop="pad"
				removeBackground={true}
				effects={[
					{
						autoContrast: true,
						vibrance: 10,
						improve: true
					},
					...(image.effects ?? [])
				]}
				overlays={image.overlays ?? []}
				src={image.src}
				alt={image.title}
			/>
		</div>
	{/each}
</div>
