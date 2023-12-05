# What We Did in Step 1 (raw images)

1. We added [Tailwind](https://tailwindcss.com/) to the project.

2. We added a [ProductGrid.svelte](./src/lib/ProductGrid.svelte) component which takes in an array of image `src`s and `title`s and displays them in a Tailwind grid.

3. We added the `images` array to the [+page.svelte](./src/routes/+page.svelte) route and filled it with some stock photos we added to the [static/product-images](./static/product-images/) folder.

   > Note: The `/src/lib/routes/+page.svelte` file is the file that is loaded in the browser when you navigate to the root of the app (`/`) by adding a subfolder such as `/about` with a new `+page.svelte` file, you would create a new route that would point to the `/about` URL.

4. We added the `ProductGrid` component to the `+page.svelte` file and passed in the `images` array.

5. We added a [+layout.svelte](./src/routes/+layout.svelte) file which is the layout for all the pages in the app and loads the Tailwind styles.

6. We have installed the `svelte-cloudinary` package, so we can have it ready for the next step.

## What to demonstrate in Step 1

The images are fairly big and they are high-res unoptimized JPGs. If you go to the Network tab in your browser's dev tools and set the throttling to "Slow 3G", you can demonstrate how slow they load.
