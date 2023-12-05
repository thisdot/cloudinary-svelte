# What We Did in Step 5 (Overlays)

1. We have added `overlays` configuration to two images in [+page.svelte](./src/routes/+page.svelte).

   - One green "New" label in the top right corner of the first image, rotated slightly.

   ```js
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
   ```

   - One orange "Sale" label in the top right corner, rotated a bit more:

   ```js
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
           ],
           ...
   ```

2. And we pass the overlays to the `CldImage` component in [ProductGrid.svelte](./src/lib/ProductGrid.svelte):

   ```html
   <CldImage overlays="{image.overlays" ?? []} ... />
   ```

## What to demonstrate in Step 5

- We have labels just from configuration :)

# What We Did in Step 4 (AI-driven image processing)

1. We modified the [ProductGrid.svelte](./src/lib/ProductGrid.svelte) `CldImage` properties to use:

   ```html
   <CldImage fillBackground="{true}" ... />
   ```

   - It's a beta feature, but now we have a nice and even grid which shows the full products on their background.

2. We also added some `effects` to the `CldImage` properties to enhance the images and make them look nicer and more consistent. We can find the list of available effects in the [Svelte Cloudinary documentation](https://svelte.cloudinary.dev/cldimage/configuration/). We used the following effects:

   ```html
   <CldImage effects={[
               {
                  autoContrast: true,
                  vibrance: 10,
                  improve: true,
               },
            ]} ... />
   ```

3. Finally, we added an option to include effects per image in [+page.svelte](./src/routes/+page.svelte) and modified the `CldImage` properties to include the individual effects as well:

   ```html
   <CldImage effects={[
               {
                  autoContrast: true,
                  vibrance: 10,
                  improve: true,
               },
               ...(image.effects ?? [])
            ]} ... />
   ```

4. And added a `color_replace` effect to the earbuds image in [+page.svelte](./src/routes/+page.svelte), so the white-ish color is replaced with gray color matching the other backgrounds. The syntax for the "replaceColor" effect is `replaceColor:<color_to_replace_with>:<tolerance>:<color_to_replace>`.

   ```js
         {
            src: 'https://res.cloudinary.com/dltsbx5b6/image/upload/v1701780641/red-bluetooth-earbuds_njubn2.jpg',
            title: 'Red bluetooth eardbuds',
            effects: [
               {
                 rreplaceColor: 'CBCBCB:20:F7F5F8'
               }
            ]
         },
   ```

## What to demonstrate in Step 4

- Now it's a nice and even grid with all the products showing in full with their backgrounds.
- We also used the `autoContrast`, `vibrance` and `improve` filters to enhance the images.
- We also used the `replaceColor` filter to replace the white-ish color in the earbuds image with gray color matching the other backgrounds.

# What We Did in Step 3 (Dynamic transformation)

1. We modified the [ProductGrid.svelte](./src/lib/ProductGrid.svelte) `CldImage` properties to use:

   ```html
   <CldImage width="{500}" height="{500}" crop="limit" ... />
   ```

   - That means we have defined a square with max dimensions of 500x500px,
   - and we are resizing the images to display in this square.

   Other possible values for `crop` to play with are:

   - `fill` - fill the square with the image, cropping the image if necessary
   - `fit` - fit the image inside the square, adding whitespace if necessary
   - `limit` - fit the image inside the square, but don't upscale it
   - `pad` - fit the image inside the square, adding whitespace if necessary, but don't upscale it

   > You can check the [interactive demo](https://cloudinary.com/documentation/resizing_and_cropping#resizing_and_cropping_interactive_demo) to see how the different crop modes work.

## What to demonstrate in Step 3

- Now the grid is nice and even. We could also show how it looks like when we change `limit` to `thumb`.
- Not all images show the full product though. We could change it to `crop="pad"`, which shows the whole products, but it feels uneven.
  - We'll address it more nicely in step 4 using the AI enabled capabilities.

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
