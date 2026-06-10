# Anthrogen Talent

Phone-friendly review UI for the [recruiting-agent](https://github.com/connorlee1/recruiting-agent)
daily sourcing system. Static page on GitHub Pages; data lives in the system's
Supabase database. Access is real auth: Supabase login (magic link or password) +
row-level security gated by the `app_users` allowlist — no privileged keys ever
touch a browser.

Two tabs:

- **Review** — each pending candidate as a card; 👍 / 🤔 / 👎 plus an optional note
  writes the verdict; the next morning's agent run folds it into the calibration.
- **Talent** — search and filter the pipeline, open anyone, move them through stages
  (contacted → interviewing → offer → hired), add author-attributed notes. The
  **+ pool** toggle also sweeps the evaluation pool (everyone the agent looked at
  and cut), with one-tap promotion into the pipeline.

Every status change is recorded in the `status_events` audit table by a database
trigger — full history of who moved whom, when.

## Setup

1. Database: run `supabase/schema.sql` (from the recruiting-agent repo) in the
   Supabase SQL editor.
2. In Supabase → Authentication → URL Configuration, set the Site URL to this app's
   URL so magic-link emails redirect back here.
3. Open the app, paste the project's **publishable/anon** key once per device
   (Project Settings → API). This key is safe to expose — RLS means it grants
   nothing without an allowlisted login.
4. Log in with your work email (magic link, or a password set in the dashboard).
5. On iPhone: Share → **Add to Home Screen** for an app-like icon.

## Adding a recruiter

Insert their email into `app_users` (dashboard table editor), then they log in.
Deleting the row revokes access.
