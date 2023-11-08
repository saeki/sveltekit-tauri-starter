# sveltekit-tauri-starter

This is a starter template for [Tauri](https://tauri.app) apps built with [SvelteKit](https://kit.svelte.dev).

Before you start, the official guide is a **must-read**: [https://tauri.app/v1/guides/getting-started/setup-sveltekit](https://tauri.app/v1/guides/getting-started/setup-sveltekit).

> **NOTE**
> This guide is for Tauri v1, but this template uses Tauri v2 alpha. The guide for Tauri v2 is not ready yet.

If something goes wrong with this template, try the official template first.

Key points of this template:

- Normal SvelteKit api routes are used.
- The frontend app can be run both as a standalone SvelteKit app and as a Tauri app.

You can develop the client app and the backend api routes with the same workflow as a normal SvelteKit app.

And then, you can build the client app as a Tauri app without any changes to the code.

Users can use both the web app and the desktop app, and the data is shared between them. Like Notion, Slack, for example. 👍

Limitations:

**SSR is not supported**. (It's a limitation of Tauri.)

If you want to use SSR, it's maybe possible with more complex setup. But this template doesn't support it to keep it simple. 😎

## Getting started

### 1. Clone this repository

```bash
git clone
```

### 2. Install dependencies

```bash
npm install
```

### 3. Run the app in development mode

```bash
npm run dev
```

then, open http://localhost:5173/

### 4. Build the app

```bash
npm run build
```

Yes, these are same workflow as a normal SvelteKit app. 😎

### 5. Run the app as a Tauri app in development mode

```bash
npm run tauri dev
```

then, the Tauri app will be launched.
also, the SvelteKit app will be launched at http://localhost:5173/

### 6. Build the app as a Tauri app

```bash
npm run tauri build
```

then, the Tauri app will be built.

If you want to cross-compile, see the official guide.

## How it works

The key trick is `.env.tauri` file that is loaded only when building the app as a Tauri app.

`npm run tauri build` runs `npm run build:tauri` internally, and `npm run build:tauri` loads `.env.tauri` file before building the app.

In `.env.tauri`, the base url for api routes defined that used in the Tauri app.

And with `.env.tauri`, `@sveltejs/adapter-static` will be used instead of `@sveltejs/adapter-node`. see `svelte.config.js`.

That's all. Happy coding! 🎉

## More examples

- [sveltekit-fastify-ws-tauri-starter](https://github.com/saeki/sveltekit-fastify-ws-tauri-starter)
