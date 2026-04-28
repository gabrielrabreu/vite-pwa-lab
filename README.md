# Vite PWA Lab

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=111111)
![Vite](https://img.shields.io/badge/Vite-8-646CFF?logo=vite&logoColor=ffffff)
![TypeScript](https://img.shields.io/badge/TypeScript-6-3178C6?logo=typescript&logoColor=ffffff)
![PWA](https://img.shields.io/badge/PWA-vite--plugin--pwa-5A0FC8)
![License](https://img.shields.io/badge/license-MIT-blue)

A simple lab with **React**, **Vite**, **TypeScript**, and
**vite-plugin-pwa** for testing a basic Progressive Web App setup.

The project intentionally stays small so it is easy to inspect what the
plugin generates: the manifest, service worker, service worker
registration, and PWA assets.

This setup is based on the official Vite PWA guide:
[vite-pwa-org.netlify.app/guide](https://vite-pwa-org.netlify.app/guide/)

---

# Running Locally

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Build for production:

```bash
npm run build
```

Preview the production build locally:

```bash
npm run preview
```

---

# Setup PWA

The main configuration lives in `vite.config.ts`.

```ts
VitePWA({
  registerType: "autoUpdate",
  includeAssets: ["favicon.ico", "apple-touch-icon.png"],
  manifest: {
    name: "Vite PWA Lab",
    short_name: "VitePWA",
    description: "Vite PWA Lab description",
    theme_color: "#ffffff",
    icons: [
      {
        src: "pwa-192x192.png",
        sizes: "192x192",
        type: "image/png",
      },
      {
        src: "pwa-512x512.png",
        sizes: "512x512",
        type: "image/png",
      },
    ],
  },
})
```

With this setup, `vite-plugin-pwa` generates the manifest, creates the
service worker, and injects the registration into the app during the
build.

`registerType: "autoUpdate"` configures the service worker to look for
updates automatically when a new build is available.

---

# Important Files

```text
vite.config.ts       Vite and VitePWA configuration
public/              PWA icons and public assets
src/App.tsx          Example React app
netlify.toml         Build, SPA redirect, and manifest header
```

---

# Validation

To validate the PWA behavior, use the production build:

```bash
npm run build
npm run preview
```

Then open the app in a browser and check DevTools:

```text
Application > Manifest
Application > Service Workers
Application > Cache Storage
```

---

# Deploy

The project already includes `netlify.toml`:

```toml
[build]
  publish = "dist"
  command = "npm run build"
```

It also includes an SPA redirect and the correct header for
`/manifest.webmanifest`.

---

# License

This project is licensed under the MIT License. See the
[LICENSE](LICENSE) file for details.
