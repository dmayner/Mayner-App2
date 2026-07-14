# Deploying / Updating the Mayner Leadership app on Netlify

You do NOT need to install anything or use a terminal. Netlify builds it for you.

## Updating an app that's ALREADY on Netlify (via GitHub)
1. Go to your GitHub repo (github.com → your "mayner-app" repo).
2. Open the src folder → click MaynerLogger.jsx → click the pencil (Edit).
3. Replace its contents with the new MaynerLogger.jsx, OR delete the file and
   upload the new one (Add file → Upload files).
   - Easiest: on the repo home, "Add file → Upload files," drag the new
     MaynerLogger.jsx into src (it overwrites), then Commit.
4. Netlify redeploys automatically in ~1 minute. Refresh your live URL.

## First-time deploy (if not done yet)
1. github.com → new repo named "mayner-app" → Create.
2. "uploading an existing file" → drag EVERYTHING in this folder in → Commit.
3. netlify.com → sign in with GitHub → Add new site → Import existing project
   → pick the repo → Deploy. You get a live URL in ~1 min.

## What this version does
- On load, it reads your REAL client list from the sheet's published CSV.
- Adding a client / logging a session writes to the sheet via the Make webhook.
- A Refresh button (top right) re-pulls the latest from the sheet.

## Two URLs live in src/MaynerLogger.jsx (near the top)
- SHEET_CSV_URL  — the published-to-web CSV the app reads from.
- WEBHOOK_URL    — the Make webhook the app writes to.
To change either, edit that line, commit, and Netlify redeploys.

## Rotate the webhook before real use
1. In Make, open the Custom webhook module, delete + recreate the hook, copy new URL.
2. Edit src/MaynerLogger.jsx, replace the WEBHOOK_URL value, commit.

## Note on the published sheet
The app reads the sheet via Google "Publish to web." Anyone with the published
CSV link can read the sheet's contents. The link is long and random, but it is
not password protected. Fine for internal use; if you need it private later,
switch to a Make "read" webhook instead.
