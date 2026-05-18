# Laman Labuh

Halaman block page statis untuk layanan DNS RPZ. Single page Astro, zero JS,
ringan untuk di-serve sebagai target redirect klien yang mengakses domain
yang ke-block.

> Domain, DNS, TLS, dan trigger deploy di-handle operator secara manual.
> Project ini hanya menghasilkan artefak statis di `dist/`.

## Stack

- [Astro](https://astro.build/) v6 — static site generator
- [Bun](https://bun.sh/) — package manager & runtime untuk script
- Vanilla CSS, tanpa framework UI
- Output: static HTML + asset, di-serve via `serve`

## Commands

| Command           | Aksi                                                             |
| :---------------- | :--------------------------------------------------------------- |
| `bun install`     | Install dependency                                               |
| `bun run dev`     | Dev server di `http://localhost:4321`                            |
| `bun run build`   | Build statis ke `dist/`                                          |
| `bun run preview` | Preview hasil build (Astro built-in)                             |
| `bun run start`   | Serve `dist/` di port `$PORT` (default `3000`) — production-like |

## Environment

| Var        | Default      | Sumber                                                |
| :--------- | :----------- | :---------------------------------------------------- |
| `PORT`     | `3000`       | Diinject platform host (Coolify/Nixpack) saat runtime |
| `NODE_ENV` | `production` | Diset di `nixpacks.toml`                              |

Tidak ada env var lain — page murni statis, tanpa API call.

## Deploy

Repo siap dideploy lewat platform Nixpack-compatible (mis. Coolify). Build
config ada di `nixpacks.toml`. Operator yang menentukan domain dan binding-nya.

## Struktur

```
.
├── public/              # static asset (logo, favicon)
├── src/
│   ├── layouts/Layout.astro
│   └── pages/index.astro
├── astro.config.mjs
├── nixpacks.toml
└── package.json
```
