# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) (or [oxc](https://oxc.rs) when used in [rolldown-vite](https://vite.dev/guide/rolldown)) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.

## CI/CD: GitHub Actions + Pages

This project includes an automated workflow to build and deploy the frontend to GitHub Pages on every push to the `main` branch.

What it does:
- Installs dependencies with `npm ci` and builds with `npm run build`.
- Sets a Vite `base` path dynamically for GitHub Pages via `DEPLOY_BASE`.
- Uploads the `dist/` folder as an artifact and deploys it to GitHub Pages.

One-time setup required in your GitHub repository:
1. Push this project to GitHub with the `.github/workflows/deploy.yml` file.
2. In GitHub → Settings → Pages:
   - Set “Source” to “GitHub Actions”.
   - Optionally configure a custom domain (then `base` will remain `/`).

Notes on Vite base path:
- If the repository is a user/org page (e.g. `username.github.io`), the workflow sets `DEPLOY_BASE=/`.
- Otherwise it sets `DEPLOY_BASE=/<repo-name>/` for project pages so assets resolve correctly.
- You can override this by setting `DEPLOY_BASE` in the workflow if you use a custom domain.

Triggering deploys:
- Any push to `main` runs the workflow and deploys automatically.
- You can also run it manually from the “Actions” tab via “Run workflow”.

Local development is unaffected; `vite.config.js` uses `DEPLOY_BASE` only when present, defaulting to `/`.
