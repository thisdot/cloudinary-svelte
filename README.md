# Cloudinary & Sveltekit Demo

## Setup

1. Checkout the repo using your favorite GIT GUI or with

   ```sh
   git clone git@github.com:thisdot/cloudinary-svelte.git
   ```

2. Install [Node.js](https://nodejs.org/en) >= 18. You can use an [installer](https://nodejs.org/en/download) or [Node Version Manager (NVM)](https://github.com/nvm-sh/nvm).

3. Install [pnpm](https://pnpm.io/) by running

   ```sh
   npm install -g pnpm
   ```

4. Install the dependencies with

   ```sh
   pnpm i
   ```

## Serving the app

Once you've installed the dependencies with `pnpm i` you can start the development server with

```sh
pnpm dev
```

or, if you want to automatically open a new browser tab, with

```sh
pnpm dev --open
```

## Building

To create a production version of the app:

```sh
pnpm build
```

You can preview the production build with `pnpm preview`.

> To deploy the app, you may need to install an [adapter](https://kit.svelte.dev/docs/adapters) for your target environment.
