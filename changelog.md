# What We Did in Step 2 (Cloudinary with auto optimization)

1. We manually uploaded our product images to Cloudinary using the [Cloudinary Console](https://console.cloudinary.com/).

2. We changed the `src`s in our `images` array in the [+page.svelte](./src/routes/+page.svelte) route to point to the cloudinary URLs instead of the local files.

   - We got the URLs from the "Media Library" in the Cloudinary Console by clicking on the `<>` icon that copies the link to the image.

3. We have added an [env.local.example](./env.local.example) file. **You'll need to copy this file, rename it to [.env.local](./.env.local) and replace `[YOUR_CLOUDINARY_CLOUD_NAME]` with the `cloud_name` value found in the [Cloudinary Console](https://console.cloudinary.com/) surrounded by quotes** (e.g. `"abcdefghij"`).

4. We modified the [ProductGrid.svelte](./src/lib/ProductGrid.svelte) component to use the `CldImage` component from [Svelte Cloudinary](https://svelte.cloudinary.dev/) instead of a plain `img` tag. It requires us to specify `width` and `height` attributes, so we have set both to `600` and set the `objectFit` attribute to `contain` to maintain the aspect ratio of our images for now.

## What to demonstrate in Step 2

- The images served from Cloudinary are now optimized for the browser and the network. If you go to the Network tab in your browser's dev tools and set the throttling to "Slow 3G", you can demonstrate how they load now and, if you switch to the previous commit, how slow they would have loaded before.

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
