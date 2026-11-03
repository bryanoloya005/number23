# GitHub Actions CI/CD Activity

This project contains the required GitHub Actions workflow for a Node.js application.

## Required workflow

`.github/workflows/ci-cd.yml`

The workflow:

1. Runs on push and pull requests targeting `main`.
2. Uses Node.js 20.
3. Runs quality gates:
   - Checkout
   - Setup Node.js
   - `npm ci`
   - `npm run lint`
   - `npm test`
4. Deploys to Vercel only after the quality gates pass and only for a push to `main`.
5. Uses the GitHub Actions secret `VERCEL_TOKEN`.

## GitHub setup

Before deployment, add your Vercel token as a repository secret:

GitHub repository → Settings → Secrets and variables → Actions → New repository secret

Name:

`VERCEL_TOKEN`

Do not place the actual token directly inside the workflow file.

## Important

The Node.js project must have these npm scripts in `package.json`:

```json
"scripts": {
  "lint": "...",
  "test": "..."
}
```

The project should also contain a valid Vercel project configuration or be compatible with Vercel's automatic project detection.
