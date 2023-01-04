## Getting Started

npx create a next app

```bash
npx create-next-app@latest --use-npm --typescript
```

Edit next.config.js file

```
/** @type {import('next').NextConfig} */

const nextConfig = {
  reactStrictMode: true,
  swcMinify: true,
  // Note: This experimental feature is required to use NextJS Image in SSG mode.
  // See https://nextjs.org/docs/messages/export-image-api for different workarounds.
  images: {
    unoptimized: true,
  },
}

module.exports = nextConfig
```

Update package.json file

```
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "export": "next export",
    "start": "next start",
    "tauri": "tauri",
    "lint": "next lint"
},
```

Install tauri cli as a dev dependency

```
npm install --save-dev @tauri-apps/cli
```

Run the following command. src-tauri folder will be generated

```
npm run tauri init
```

Fill out the answers like this:

What is your app name?
This will be the name of your final bundle and what the OS will call your app. You can use any name you want here.

What should the window title be?
This will be the title of the default main window. You can use any title you want here.

Where are your web assets (HTML/CSS/JS) located relative to the <current dir>/src-tauri/tauri.conf.json file that will be created?
This is the path that Tauri will load your frontend assets from when building for production.
Use ../out for this value.

What is the URL of your dev server?
This can be either a URL or a file path that Tauri will load during development.
Use http://localhost:3000 for this value.

What is your frontend dev command?
This is the command used to start your frontend dev server.
Use npm run dev for this value.

What is your frontend build command?
This is the command to build your frontend files.
Use npm run build && npm run export for this value.

Make sure your src-tauri/tauri.conf.json looks like this

```
{
  "build": {
    "beforeBuildCommand": "npm run build && npm run export",
    "beforeDevCommand": "npm run dev",
    "devPath": "http://localhost:3000",
    "distDir": "../out"
},
```

Finally,

```
npm run tauri dev
```

