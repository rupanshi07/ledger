# Ledger

A small single-file web app for tracking **assignments** and **projects**, with one twist: project steps can automatically move their deadline earlier if you finish a step ahead of schedule and nothing else is competing for that time.

**[Live demo →](#)** *(replace with your GitHub Pages link once enabled — see below)*

## What it does

- **Assignments** — subject, submission date, mark complete.
- **Projects** — a list of steps, each with its own deadline. A progress bar tracks % complete.
- **Self-tightening schedule** — finish a step early, and the app checks every other pending deadline you have (other steps, other projects, other assignments). If nothing else is due in the gap that opened up, it pulls the *next* step's deadline forward by the days you saved. Your original date is kept and shown as a **buffer**, never deleted — just no longer the active target.
- **Profiles** — a lightweight, password-less way to keep separate task lists per name. See "About accounts" below before relying on this for anything real.

## Running it

It's a single static HTML file with no build step and no server.

```bash
git clone https://github.com/<your-username>/ledger.git
cd ledger
# just open it
open index.html   # macOS
# or: xdg-open index.html   # Linux
# or: start index.html      # Windows
```

Or double-click `index.html` in a file browser.

## Hosting it for free (GitHub Pages)

1. Push this repo to GitHub (see below).
2. Go to **Settings → Pages** on the repo.
3. Under "Build and deployment," set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Save. Your app will be live at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

## About accounts

This version's "sign in" is a name-only profile switcher — there's no password and no server. It's meant to demonstrate the idea of separate task lists per person, not to be secure. If you want real accounts, you'd want to add a backend (e.g. Supabase, Firebase, or your own API) with proper authentication, and swap out the storage layer this app currently uses for calls to that backend.

## Tech

Plain HTML/CSS/JavaScript. No framework, no dependencies, no build tooling. Data is stored in the browser's `localStorage`, so it's per-browser/per-device — clearing site data or switching browsers loses it. Swap `saveTasks()` / `loadTasks()` in `index.html` for calls to a real backend if you want accounts that sync across devices.

## License

MIT — see [LICENSE](LICENSE). Contributions welcome.
