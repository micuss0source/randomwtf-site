# Random What Tha Farm — Site Files

Everything you need to get randomwtf.com live. No coding required, just uploading and clicking.

## What's in here

- `index.html` — the homepage
- `style.css` — shared styling for post pages
- `posts.json` — the list of posts (this is what makes "Today's Pick" rotate)
- `posts/` — folder with individual post pages, plus an archive page (`posts/index.html`)
- `CNAME` — tells GitHub this site belongs to randomwtf.com (don't delete or rename this file)

## Step 1: Upload the files to GitHub

1. Go to your `randomwtf-site` repository on GitHub.
2. Click **Add file → Upload files**.
3. Drag in ALL of these files and folders, keeping the same names:
   - `index.html`
   - `style.css`
   - `posts.json`
   - `CNAME`
   - the whole `posts` folder (drag the folder itself, GitHub will keep it as a folder)
4. Scroll down, click **Commit changes**.

## Step 2: Turn on GitHub Pages

1. In the repo, click **Settings** (top tab).
2. Click **Pages** in the left sidebar.
3. Under "Build and deployment" → Source, choose **Deploy from a branch**.
4. Branch: pick **main**, folder: **/ (root)**. Click **Save**.
5. GitHub will give you a link like `https://yourusername.github.io/randomwtf-site/` — that's a temporary preview, ignore it for now.
6. Still on this page, scroll to **Custom domain**, type in `randomwtf.com`, click **Save**. (This works together with the CNAME file you already uploaded.)

## Step 3: Point GoDaddy at GitHub

In GoDaddy, go to your domain's **DNS Management** for randomwtf.com and add/edit these records:

**A records** (delete any existing A records pointing elsewhere first) — add all four:

| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

**CNAME record** (for the www version):

| Type | Name | Value |
|------|------|-------|
| CNAME | www | yourusername.github.io |

(Swap `yourusername` for your actual GitHub username.)

Save. DNS changes usually show up within 10-60 minutes, occasionally up to a day.

## Step 4: Turn on "Enforce HTTPS"

Once the DNS has propagated (you can check by just visiting randomwtf.com), go back to Settings → Pages and check the box for **Enforce HTTPS**. This makes sure visitors get the secure padlock.

## About the repair contact form

Right now the form on the homepage won't actually send you anything — it's wired up to `https://formspree.io/f/YOUR_FORM_ID`, a placeholder. To make it real:

1. Go to formspree.io and make a free account (50 submissions/month free, plenty to start).
2. Create a new form, it'll give you a form ID/URL.
3. Open `index.html`, find the line that says `action="https://formspree.io/f/YOUR_FORM_ID"`, and swap in your real form URL.
4. Re-upload `index.html` to GitHub (same Upload files step, it'll ask to overwrite).

Until you do this step, the form will look right but submissions will fail — so this one matters.

## Adding a new post later

1. Duplicate one of the files in `posts/` as a starting template, rename it, and change the title/body text.
2. Open `posts.json` and add a new entry at the bottom, matching the format of the existing ones — slug, title, kind, excerpt, and the url pointing to your new file.
3. Upload both to GitHub. The homepage's "Today's Pick" and the archive page will pick it up automatically — no other changes needed.
