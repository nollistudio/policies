# NS_POLICIES — Nollistudio public policy pages

Static site hosting Nollistudio's user-facing policy documents, required by Meta App Review for the Nolli Scheduler (App ID `1499900481550107`).

**What's here:**

| File | Purpose |
|---|---|
| `index.html` | Landing page listing every policy |
| `privacy.html` | Privacy Policy |
| `terms.html` | Terms of Service |
| `data-deletion.html` | Data Deletion Instructions |
| `.nojekyll` | Disables GitHub Pages' Jekyll processing so everything ships as plain HTML |
| `README.md` | This file — deployment guide |

**Source of truth** = this Dropbox folder (`NOLLISTUDIO Dropbox/NS_ECOSYSTEM/NS_POLICIES/`). **Public URL** = GitHub Pages deployment. Edit here, push to GitHub, Pages rebuilds automatically.

## Deploy in three clicks (first time)

1. **Create a new public GitHub repo** at <https://github.com/new>
   - Repository name: `policies` (suggested; anything works)
   - Owner: the Nollistudio org, or the personal account that owns Meta App `1499900481550107`
   - Visibility: **Public** (required for GitHub Pages)
   - Tick *Add a README* — we'll overwrite it
   - Click **Create repository**

2. **Upload every file from this folder** to the repo
   - On the new repo page, click **Add file → Upload files**
   - Drag all 5 files (`index.html`, `privacy.html`, `terms.html`, `data-deletion.html`, `.nojekyll`) into the drop zone (you can also drag `README.md` — doesn't hurt, it won't render on the public site)
   - Commit directly to `main`

3. **Enable GitHub Pages**
   - Repo → **Settings** → **Pages** (left sidebar)
   - Under *Build and deployment* → *Source* → select **Deploy from a branch**
   - **Branch**: `main`, **Folder**: `/ (root)` → click **Save**
   - Wait ~30 seconds. Refresh the Pages settings page. You'll see:
     > Your site is live at `https://<owner>.github.io/policies/`

**That URL is what goes into Meta App Review.**

## URL mapping for Meta App Review

Paste these into **App Settings → Basic**:

| Meta field | URL |
|---|---|
| Privacy Policy URL | `https://<owner>.github.io/policies/privacy.html` |
| Terms of Service URL | `https://<owner>.github.io/policies/terms.html` |
| Data Deletion Instructions URL | `https://<owner>.github.io/policies/data-deletion.html` |
| App Homepage URL (optional) | `https://<owner>.github.io/policies/` |

Replace `<owner>` with the actual GitHub owner (e.g. `nollistudio` if that's the org name). You can confirm the URL by clicking the link GitHub Pages shows in the Settings page after step 3.

## Updating a policy

1. Edit the relevant `.html` file in this Dropbox folder (content lives between `<main>…</main>`).
2. Update the `Last updated` date inside the page.
3. On GitHub, open the file → pencil icon → paste the new content → commit to `main`. Pages redeploys in ~30s.

Alternatively, if you set up `git clone` locally, you can just `git push` from this folder — but uploading via the web UI works fine for infrequent edits.

## Custom domain (optional, later)

If you want `policies.nollistudio.com` instead of the default `github.io` URL:

1. Repo → Settings → Pages → **Custom domain** → type `policies.nollistudio.com` → Save.
2. In your DNS provider, add a **CNAME** record: `policies` → `<owner>.github.io`.
3. Wait ~10 minutes for DNS propagation, then tick **Enforce HTTPS** on the Pages settings.
4. Update the URLs in Meta App Review.

No code changes needed — all inter-page links in these files use relative paths.

## Why this lives in NS_ECOSYSTEM

`NS_ECOSYSTEM/` is Nollistudio's catch-all for cross-app documentation (see `README.md`, `BROADCASTS.md`, `APP_IDEAS.md`). Public-facing policy documents belong here because they're cross-cutting — one Privacy Policy covers every Nolli app that connects to third-party APIs (Scheduler, Moodboard, Shorts Creator, VB Designer). When new apps come online, add their data-access details to `privacy.html` rather than standing up a new site per app.
