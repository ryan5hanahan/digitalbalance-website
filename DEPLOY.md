# Deploying digitalbalance.app via Cloudflare Workers

The site is static files in `public/`, served by the Cloudflare Worker
`digitalbalance-app` (Workers & Pages → digitalbalance-app). There is no build step.

## Updating the site
- Push to the `master` branch of this repo
- Workers Builds runs `npx wrangler deploy` and the site updates within a minute

## What gets published
`wrangler.jsonc` sets the assets directory to `public/`, so only that folder is
uploaded. Keep everything that isn't part of the site (this file, `.gitignore`,
notes) outside it. Without the config, wrangler served the whole repo, `.git` included.

The `name` in `wrangler.jsonc` must match the Worker's name in the dashboard.

## Dashboard settings (Settings → Build)
- Git repository: `ryan5hanahan/digitalbalance-website`, production branch `master`
- Build command: none
- Deploy command: `npx wrangler deploy`
- Root directory: `/`

## Custom domain
Domains tab → `digitalbalance.app` (HTTPS is automatic).
