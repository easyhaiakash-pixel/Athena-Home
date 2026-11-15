# How to put Athena's Home online (free)

The site is plain files, so any free static host works. Nothing has been published yet; you decide when.

Before you publish: check `data/items.json` (links, gifted/wish) and `data/athena.json` (age, day).

## Option 1: Netlify Drop (easiest, 2 minutes)
1. Go to https://app.netlify.com/drop and log in (free account).
2. In Finder, open `~/personal/one-life/`.
3. Drag the whole **`athena-home`** folder onto the Netlify page.
4. Wait about 20 seconds. Netlify gives you a link like `https://something-123.netlify.app`.
5. Rename it: **Site configuration → Change site name** → for example `athenas-home` → link becomes `https://athenas-home.netlify.app`.
6. Put that link in your Instagram bio / Linktree.

**To update later** (new gift, new day): Netlify → your site → **Deploys** → drag the `athena-home` folder onto the "Drag and drop your site output folder here" box again. The link stays the same.

## Option 2: GitHub Pages
1. Make a free GitHub account and a new **public** repository called `athenas-home`.
2. On the repository page: **Add file → Upload files** → drag in everything **inside** `athena-home` (index.html, css, data, fonts, src, vendor, and the .md files). Click **Commit changes**.
3. **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main`, folder `/ (root)` → **Save**.
4. After about 1 minute the site is at `https://YOUR-NAME.github.io/athenas-home/`.

**To update later:** upload the changed file (usually `data/items.json`) again with **Add file → Upload files**, then **Commit changes**.

## After publishing, check on your phone
- Open the link from Instagram (DM it to yourself and tap it), so you test the Instagram in-app browser.
- Tap a gift: the card opens and the Amazon button opens the right product.
- Open a gift card: the line "As an Amazon Associate I earn from qualifying purchases." is under the buttons.

## Amazon rules to keep
- Never add prices or Amazon product photos.
- Keep the disclosure line (it is built into every gift card and the gift wall). Amazon requires it; do not delete it.
- Add the website address to your Amazon Associates account (US and India) under the list of your websites, so Amazon knows the links come from your site.
