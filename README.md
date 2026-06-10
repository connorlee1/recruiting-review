# Anthrogen Talent

Phone-friendly review UI for the [recruiting-agent](https://github.com/connorlee1/recruiting-agent)
daily sourcing system. Static page, no backend of its own: it talks directly to the
system's Supabase database with credentials stored only in the browser's localStorage.

Two tabs:

- **Review** — each pending candidate as a card; 👍 / 🤔 / 👎 plus an optional note
  writes the verdict to the database, and the next morning's agent run folds it into
  the calibration.
- **Talent** — search and filter everyone in the pipeline, open anyone, move them
  through stages (contacted → interviewing → offer → hired), add notes. The
  **+ pool** toggle also sweeps the evaluation pool (everyone the agent looked at
  and cut), with one-tap promotion into the pipeline.

## One-time setup

1. Set up the database: run `supabase/schema.sql` from the recruiting-agent repo in
   your Supabase project's SQL editor.
2. Open the app, paste the project URL and the **service_role** key
   (Supabase dashboard → Project Settings → API), Connect.
3. On iPhone: Share → **Add to Home Screen** for an app-like icon.

The service_role key bypasses row-level security — only enter it on your own devices.
This repo contains no candidate data and no secrets — only the generic UI.
