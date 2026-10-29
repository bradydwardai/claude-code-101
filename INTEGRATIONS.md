# Integrations — Claude Code 101

RPG-styled learning platform for Claude Code: a static web portal (`web/`), a local install script, and optional anonymized progress sync.

Ship rule: branch → PR → mint (gitleaks) → merge. No CI. Main is judged every 10 min; deploys and fleet pulls follow green-main only.

## Active Integrations

- **GitHub Pages** — serves the portal at `https://bradydwardai.github.io/claude-code-101/` from `main` (`/`, legacy build). This is the one GitHub-hosted deploy left after the exit: Pages builds from the branch itself, not from Actions, so it still publishes with Actions OFF. Owner: GitHub account `bradydwardai`. Public repo.
- **Supabase (project "Claude code 101", ref `uzqjklfkdvxutjdpahpn`)** — consent-gated question logging, graduate status and the analytics dashboard (`web/analytics-dashboard.html`, Realtime aggregates). Env names: `SUPABASE_URL`, `SUPABASE_ANON_KEY`, `SUPABASE_SERVICE_ROLE_KEY`, `QUESTION_SYNC_ENABLED` (`.env.example`). Migrations and edge functions under `supabase/`. **Status: the project is INACTIVE (paused) in the Supabase dashboard** — sync and the dashboard are off until it is restored. It sits in a different Supabase org (`txqlbgxnnkmfbdhmqinr`) from every other Brady project (`sjtwhbghuigawtnwmgtg`). Owner: unverified (confirm which login owns that org before restoring).
- **Anthropic API** — `ANTHROPIC_API_KEY` for the install script's optional checks and sample generations. Owner: unverified (no key for this repo is stored in dotfiles sops; a learner supplies their own).

## GitHub repo

`bradydwardai/claude-code-101`, public, no webhooks. `.github/workflows/ci.yml` is a no-op echo and Actions is OFF; leave it or delete it in the old-name sweep.

## Not used

- No Vercel, no Railway, no Cloudflare, no payments, no analytics vendor (the dashboard reads Supabase directly).
