# Fels Cave

A browser-based WebGL experience of Fels Cave, built in Unity and deployed as a
static site to GitHub Pages. The page shows a short intro, plays a video preview,
then loads the Unity build, which runs entirely in the browser via WebAssembly.

The live site is at <https://anucybernetics.github.io/fels-cave/>.

## About

This experience was built by an ANU TechLauncher student team. Direct all
enquiries to <ash.lenton@anu.edu.au>.

## Deployment

The site is static and deploys to GitHub Pages via `.github/workflows/deploy.yml`
on every push to `main`. There is no build step: the files are served as-is, with
a `.nojekyll` marker so GitHub Pages skips Jekyll processing.

## Structure

- `index.html` --- the intro / video / game wrapper (vanilla JS, no framework)
- `web_build/` --- the Unity WebGL build (engine `.wasm`, asset `.data`, loader)
- `fels-cave-outside.mp4` --- the video preview

## Local preview

Serve the directory with any static file server, then open the printed URL:

```sh
python3 -m http.server 8000
```

A plain file server is enough; the experience has no backend.

## A note on size

The Unity build is large (~130 MB of `.wasm` + `.data`), so the first load
transfers a correspondingly large payload before the cave scene appears.
