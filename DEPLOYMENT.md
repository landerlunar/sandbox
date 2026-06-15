# GLP-1 Macro Coach — How It's Built & Deployed

A plain-language reference for how this app is set up, hosted, and updated.

## What the app is

A single web page (`index.html`) — a personal GLP-1 nutrition tool with:
- A macro calculator (calories + protein-forward targets)
- A daily vitamin/supplement tracker (with % of target)
- A weight "journey" chart
- Google sign-in + cloud sync so data follows you across devices

There is no separate "server" we run — the page is static, and Firebase provides the
login + database behind it.

## High-level: what we set up and how

| Piece | What it does | How it's set up | Where it lives |
|---|---|---|---|
| **The app** | The actual page you use | One file, `index.html` (HTML + CSS + JavaScript, no build step) | This repo |
| **Git** | Saves snapshots of the code | `git add` → `git commit` → `git push` | Local + GitHub |
| **GitHub repo** | Online home for the code | `github.com/landerlunar/sandbox` (public) | GitHub |
| **GitHub Pages** | Hosts the page on the internet for free | Enabled to serve the `main` branch root | `landerlunar.github.io/sandbox/` |
| **Firebase Auth** | "Sign in with Google" | Google provider enabled; `landerlunar.github.io` authorized | Firebase project `glp1-macro-coach` |
| **Firestore** | Cloud database that syncs your data | One document per user at `users/{your-id}`; rules let only you read/write yours | Firebase |
| **On-device storage** | Works offline + instant | Browser `localStorage`, kept in sync with Firestore | Each device |

## How data sync works (simple version)

1. You use the app → changes save instantly to that device (`localStorage`).
2. If you're signed in, the same changes are pushed up to **Firestore** (the cloud).
3. Any other device you're signed into hears the change live and updates itself.
4. Your data is private: the security rules only let *you* read/write *your* record.

## Deployment process (how a change goes live)

Every update follows the same loop:

```
1. Edit index.html        (make the change)
2. git add .              (gather the change)
3. git commit -m "..."    (save a labeled snapshot)
4. git push               (send it to GitHub)
5. GitHub Pages rebuilds  (~1 minute, automatic)
6. Live at the URL        (https://landerlunar.github.io/sandbox/)
```

No manual "publish" step — pushing to GitHub *is* the deploy.

## How to test after a change

- **Quick local look:** open `index.html` on the Mac (note: Google sign-in only works on
  the live URL, not the local file).
- **Automated checks** (no browser needed):
  - JavaScript has no syntax errors
  - All key page sections are present
  - The live site's code matches the local code (checksum compare)
  - GitHub Pages reports build status "built"
- **Manual checks** (need the live site + your login):
  - Sign in with Google shows "Synced as …"
  - A weight logged on one device appears on another
  - % badges and the weight chart update correctly

## Key addresses

- **Live app:** https://landerlunar.github.io/sandbox/
- **Code:** https://github.com/landerlunar/sandbox
- **Firebase console:** https://console.firebase.google.com/ (project `glp1-macro-coach`)
- **Local copy:** `~/Projects/sandbox`
