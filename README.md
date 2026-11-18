# HUMAN FACTORY — public media

Public screenshots and a short gameplay video of **HUMAN FACTORY** (co-op industrial dark-comedy game), used by the demo site as static storage.
The game code lives elsewhere; this repo holds **only media**. Layout is versioned, files are never overwritten (add a new `0.x.y` folder instead).

```
human-factory/0.10.0/
  manifest.json                         <- sizes, sha256, dimensions, captions (machine readable)
  poster.jpg                            <- video poster, 1920x1080
  video/human-factory-showcase-1080p.mp4   (11.8 MB, 20 s, H.264, no audio)
  video/human-factory-showcase-720p.mp4    ( 5.0 MB, 20 s, H.264, no audio)
  video/human-factory-trailer-1080p.mp4    (15.5 MB, 28 s, titled trailer, no audio)
  video/human-factory-trailer-720p.mp4     ( 7.0 MB, 28 s)
  trailer-poster.jpg                       <- trailer poster, 1920x1080
  photo/photo-01-hud.jpg … photo-04-assembler.jpg   (1920x1080)
  thumb/thumb-01-hud.jpg … thumb-04-assembler.jpg   (640x360)
```

## Game downloads

The playable builds are **not** in the git tree: they are assets of the GitHub Release `hf-0.10.0`
(`HUMAN-FACTORY-0.10.0-Windows-x64.zip`, `HUMAN-FACTORY-0.10.0-macOS-AppleSilicon.zip`, each with a `.sha256`).
The site links to `/api/v1/download/<game>/<build>`, which counts the click and redirects to the release asset.

## URLs for the site

Set the site's media base URL (e.g. `MEDIA_BASE_URL`) to one of:

| Option | Base URL | Notes |
| --- | --- | --- |
| jsDelivr CDN (recommended) | `https://cdn.jsdelivr.net/gh/daulet-kushek-narxoz/illegal-factory-public-resource@hf-0.10.0-r2/` | CDN cache, proper range requests for video, immutable when pinned to the tag; files must stay under 20 MB |
| raw.githubusercontent | `https://raw.githubusercontent.com/daulet-kushek-narxoz/illegal-factory-public-resource/main/` | no CDN, rate limited; fine for a demo |

Example: `<video src="{BASE}human-factory/0.10.0/video/human-factory-showcase-1080p.mp4" poster="{BASE}human-factory/0.10.0/poster.jpg" muted playsinline controls preload="metadata">`

## Limits to keep in mind

GitHub is not object storage: single file < 100 MB (this repo keeps files < 20 MB for jsDelivr), repository recommended < 1 GB, no private access, no signed URLs, no custom CORS/cache headers.
For large game builds or many videos move the files to S3-compatible storage (Cloudflare R2, Backblaze B2) and change only the base URL.

All rights reserved by the project owner unless stated otherwise.
