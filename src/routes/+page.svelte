<script>
	import ProductGrid from '../lib/ProductGrid.svelte';

	const images = [
		{ src: '/product-images/black-fashion-backpack.jpg', title: 'Black fashion backpack' },
		{ src: '/product-images/blue-t-shirt.jpg', title: 'Blue t shirt' },
		{
			src: '/product-images/bright-red-purse-with-gold.jpg',
			title: 'Bright red purse with gold'
		},
		{ src: '/product-images/dainty-gold-necklace.jpg', title: 'Dainty gold necklace' },
		{ src: '/product-images/light-green-t-shirt.jpg', title: 'Light green t shirt' },
		{ src: '/product-images/red-bluetooth-earbuds.jpg', title: 'Red bluetooth eardbuds' },
		{ src: '/product-images/purple-t-shirt.jpg', title: 'Purple t shirt' },
		{ src: '/product-images/red-t-shirt.jpg', title: 'Red t shirt' }
	];
</script>

<ProductGrid {images} />
