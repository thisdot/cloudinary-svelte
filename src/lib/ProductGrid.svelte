<script>
	/**
	 * @type {{ src: string, title: string }[]}
	 */
	export let images = [];
</script>

<div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 p-4">
	{#each images as image}
		<div class="overflow-hidden rounded-lg">
			<img src={image.src} alt={image.title} />
		</div>
	{/each}
</div>
