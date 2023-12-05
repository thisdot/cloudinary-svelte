<script>
	import ProductGrid from '../lib/ProductGrid.svelte';

	const images = [
		{
			src: 'https://res.cloudinary.com/dltsbx5b6/image/upload/v1701773749/yjmrebikn9bbskv80gki.jpg',
			title: 'Black fashion backpack'
		},
		{
			src: 'https://res.cloudinary.com/dltsbx5b6/image/upload/v1701773752/dzhwhjrwxjpj3dzufhk7.jpg',
			title: 'Blue t shirt'
		},
		{
			src: 'https://res.cloudinary.com/dltsbx5b6/image/upload/v1701773752/w66suwxav7q7vmd5eqjc.jpg',
			title: 'Bright red purse with gold',
			overlays: [
				{
					text: {
						text: 'New!',
						fontSize: 18,
						fontWeight: 'bold',
						fontFamily: 'Montserrat',
						color: 'white',
						letterSpacing: 3
					},
					position: {
						gravity: 'north_east',
						y: 20,
						x: 20,
						angle: -18
					},
					effects: [
						{
							background: 'green',
							crop: 'lpad',
							radius: 'max',
							width: 80,
							height: 80
						}
					]
				}
			]
		},
		{
			src: 'https://res.cloudinary.com/dltsbx5b6/image/upload/v1701773748/m8ef4mansuf0t2t2a7an.jpg',
			title: 'Dainty gold necklace'
		},
		{
			src: 'https://res.cloudinary.com/dltsbx5b6/image/upload/v1701773752/mymvjorkexo0cbr36asm.jpg',
			title: 'Light green t shirt'
		},
		{
			src: 'https://res.cloudinary.com/dltsbx5b6/image/upload/v1701780641/red-bluetooth-earbuds_njubn2.jpg',
			title: 'Red bluetooth eardbuds',
			overlays: [
				{
					text: {
						text: 'Sale!',
						fontSize: 20,
						fontWeight: 'bold',
						fontFamily: 'Montserrat',
						color: 'white',
						letterSpacing: 3
					},
					position: {
						gravity: 'north_east',
						y: 20,
						x: 20,
						angle: 45
					},
					effects: [
						{
							background: 'orange',
							crop: 'lpad',
							radius: 'max',
							width: 100,
							height: 100
						}
					]
				}
			]
		},
		{
			src: 'https://res.cloudinary.com/dltsbx5b6/image/upload/v1701773754/hjrmnntcis3kvl09bhx7.jpg',
			title: 'Purple t shirt'
		},
		{
			src: 'https://res.cloudinary.com/dltsbx5b6/image/upload/v1701773753/pbvkxoqtoy0n9xx2wi6z.jpg',
			title: 'Red t shirt'
		}
	];
</script>

<ProductGrid {images} />
