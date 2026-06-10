# Candidate Review

Phone-friendly review UI for the [recruiting-agent](https://github.com/connorlee1/recruiting-agent)
daily sourcing system. Static page, no backend: it talks to the private repo directly
via the GitHub API with a fine-grained token stored only in the browser's localStorage.

Two tabs, both backed by `candidates/db.json` in the private repo (the talent
database — one record per candidate ever sourced, with pipeline status and notes):

- **Review** — each pending candidate as a card; 👍 / 🤔 / 👎 plus an optional note
  commits the verdict to `main`, and the next morning's agent run folds it into the
  calibration.
- **Talent** — search and filter everyone ever sourced, open anyone, move them
  through the pipeline (contacted → interviewing → offer → hired), add notes.

## One-time setup

1. Create a [fine-grained token](https://github.com/settings/personal-access-tokens/new):
   Repository access → **only** `connorlee1/recruiting-agent`; Permissions →
   **Contents: Read and write**.
2. Open the app, paste the token, Connect.
3. On iPhone: Share → **Add to Home Screen** for an app-like icon.

This repo contains no candidate data and no secrets — only the generic UI.
