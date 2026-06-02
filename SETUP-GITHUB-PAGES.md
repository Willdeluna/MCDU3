# Hosting this fork on GitHub Pages

This is a fork of VirtualCDU / RFMC (MIT licensed — original at
github.com/Reedtrullz/RFMC). The `LICENSE` file is unchanged and must stay.

## What was changed from upstream (3 things)

1. **`vite.config.ts`** — added `base: process.env.BASE_PATH || '/'` so the
   build can be served from a subpath like `/<repo>/`. Local dev is unaffected.
2. **Removed `.github/workflows/deploy.yml`** — it SSHed into the original
   author's private VPS and can't work on your fork.
3. **Added `.github/workflows/deploy-pages.yml`** — builds and publishes to
   GitHub Pages with no secrets or servers needed.

Everything else is the original project.

## Deploy steps

1. Create a new repo on GitHub and push this folder to the `main` branch.
2. In the repo: **Settings > Pages > Source: "GitHub Actions"**.
3. Push (or run the "Deploy to GitHub Pages" workflow manually from the
   Actions tab). When it finishes, your live URL is:
   `https://<your-username>.github.io/<repo-name>/`
4. Open that URL in a browser — including on your work PC.

## Notes

- The app is fully client-side; the optional MSFS/PMDG WebSocket bridge in
  `server/` is not part of the Pages build and isn't needed to use the trainer.
- The leftover `ci.yml` workflow runs tests on push and may show a red X on
  your fork; it's harmless and independent of the Pages deploy. You can disable
  it under Settings > Actions if the noise bothers you.
- First HTTPS load lets the service worker cache the app for offline use.
