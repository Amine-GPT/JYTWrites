# Writer Portfolio Site

A minimal, editorial 5-page portfolio site for a writer — modeled on the layout of another writer. Pure HTML + CSS. No build step, no framework, no tracking. Easy to edit, free to host on GitHub Pages.

The site currently ships populated with sample content for a fictional writer ("Jess Merrow") so you can see what it looks like filled in. Replacing that with your partner's real content is a find-and-replace job.

---

## 📁 What's in this folder

```
index.html          Home
about.html          About
films.html          Short Films (with embed-ready film cards)
books.html          Books & Essays
contact.html        Contact
styles.css          All styling — edit colors/fonts here
images/             Placeholder SVG images (swap for real photos)
README.md           This file
```

Every editable part of the site is marked with a comment like this:

```html
<!-- EDIT: your name -->
```

Open any `.html` file and search for `EDIT:` to find every spot that needs changing.

---

## ✏️ Part 1 — Editing the content

You only need a plain text editor. I recommend **VS Code** (free): <https://code.visualstudio.com/>.

### Step 1. Preview locally
Double-click `index.html`. It opens in your browser. Edit a file, save, refresh the browser.

### Step 2. Change the text
Open any `.html` file and look for `<!-- EDIT: ... -->` comments. The line directly below each comment is the thing to change. Example:

```html
<!-- EDIT: her name -->
<a class="brand" href="index.html">Jess Merrow</a>
```

Change `Jess Merrow` to your partner's name. Save. Refresh. Done. Every page uses the same header/footer structure, so you'll repeat this swap once per page (5 times total per shared field like name or email).

### Step 3. Replace the placeholder images
The `images/` folder contains 6 elegant SVG placeholders (warm monochrome gradients with soft grain) so the site looks intentional until real photos exist. To replace them:

1. Drop real photos into `images/` — keep the same filenames to avoid editing HTML:
   - `hero.jpg` — homepage portrait (tall, 3:4 ratio, at least 900×1200px)
   - `about-1.jpg`, `about-2.jpg` — about page (4:5 ratio works well)
   - `film-softboiled.jpg`, `film-glasseye.jpg`, `film-quiet.jpg` — film posters (4:3 ratio)

2. In each HTML file where the image is referenced, change the `.svg` extension to `.jpg`:
   ```html
   <img src="images/hero.svg" ...>     →    <img src="images/hero.jpg" ...>
   ```

Or use completely different filenames — just update the `src="..."` to match.

### Step 4. Add or remove films
Open `films.html`. Each `<article class="film">...</article>` block is ONE film. Copy the whole block and paste to add more. Delete a block to remove one.

Each film card can show one of three things — pick one per film:

- **Poster + external link** — static image that links out to Vimeo/YouTube (fastest, default)
- **Vimeo embed** — video plays inline on your page. Get the embed URL from Vimeo's *Share → Embed* dialog (it looks like `https://player.vimeo.com/video/123456789`)
- **YouTube embed** — same idea. *Share → Embed* on YouTube (URL looks like `https://www.youtube.com/embed/XXXXXXXXXXX`)

Film 1 in the template shows the poster-plus-link style. Film 2 has a commented-out Vimeo embed showing exactly how to swap a poster for an inline video player. Film 3 is a "Contact to Watch" variation for password-protected films.

### Step 5. Add or remove books
Open `books.html`. Same pattern — each `<article class="work">` is one book/project. Copy/paste to add, delete to remove. The "Published Essays" section below is a simple list — copy an `<li>` to add another essay.

### Step 6. Change colors or fonts globally
Open `styles.css`. The top block has everything:

```css
:root {
  --paper:    #F7F3EC;   /* page background */
  --ink:      #181613;   /* main text */
  --ink-soft: #5A544B;   /* secondary text */
  --display:  "Fraunces", ...;       /* headings */
  --sans:     "Instrument Sans", ...; /* body text */
}
```

Change those and the whole site updates. For different fonts, pick from [Google Fonts](https://fonts.google.com/), grab the `<link>` URL from their "Get embed code" panel, replace the existing `<link href="https://fonts.googleapis.com/...">` in each HTML file, then update `--display` or `--sans` in `styles.css` to match the new family name.

---

## 🚀 Part 2 — Putting it on the internet with GitHub Pages (free)

GitHub Pages hosts static sites like this one for free at `https://YOUR-USERNAME.github.io/REPO-NAME/`.

### Step 1. Make a GitHub account
<https://github.com/signup>. Free.

### Step 2. Install GitHub Desktop
Download: <https://desktop.github.com/>. Sign in. This saves you from learning git commands.

### Step 3. Create the repository
1. In GitHub Desktop: **File → New Repository**.
2. Name it something simple — `partner-site` or `jess-merrow-site`. (This name will appear in the URL until you add a custom domain.)
3. Pick a local path on your computer.
4. Click **Create Repository**.
5. GitHub Desktop opens the new empty folder — copy all your site files (the `.html` files, `styles.css`, `images/` folder, this README) into that folder.
6. Back in GitHub Desktop, you'll see all the files listed. At the bottom-left, type a commit message like `first commit` and click **Commit to main**.
7. Click **Publish repository** at the top. Leave "Keep this code private" unchecked (public is simplest for free Pages). Click **Publish Repository**.

### Step 4. Turn on GitHub Pages
1. In your browser, go to `https://github.com/YOUR-USERNAME/REPO-NAME`.
2. Click **Settings** (top-right of the repo navigation).
3. In the left sidebar, click **Pages**.
4. Under **Source**, set:
   - **Branch:** `main`
   - **Folder:** `/ (root)`
5. Click **Save**.
6. Wait 30–90 seconds. Refresh the page. A green box appears with the live URL: `https://YOUR-USERNAME.github.io/REPO-NAME/`

The site is live.

### Step 5. Updating the site later
Whenever you edit a file:
1. Save the file.
2. Open GitHub Desktop — your changes appear automatically in the left panel.
3. Type a short message like `updated bio`, click **Commit to main**.
4. Click **Push origin** at the top.
5. Wait ~30 seconds. The live site updates automatically.

---

## 🌐 Part 3 — Connecting a custom domain (e.g. `hername.com`)

When you're ready to use her own domain instead of the `github.io` URL:

### Step 1. Buy the domain
Any registrar works — **Cloudflare Registrar** (cheapest, no markup), **Namecheap**, or **Porkbun**. Expect ~$10–15/year for `.com`.

### Step 2. Tell GitHub about the domain
In repo **Settings → Pages → Custom domain**, type `hername.com` and click **Save**. GitHub creates a file called `CNAME` in the repo automatically.

### Step 3. Point the domain at GitHub (DNS)
Log in to wherever you bought the domain. Find **DNS settings** (sometimes "DNS records" or "Advanced DNS"). Add these records:

**For the apex domain (`hername.com`)** — four A records pointing to GitHub's IPs:

| Type | Host / Name | Value             |
|------|-------------|-------------------|
| A    | `@`         | `185.199.108.153` |
| A    | `@`         | `185.199.109.153` |
| A    | `@`         | `185.199.110.153` |
| A    | `@`         | `185.199.111.153` |

**For `www.hername.com`** — one CNAME record:

| Type  | Host / Name | Value                      |
|-------|-------------|----------------------------|
| CNAME | `www`       | `YOUR-USERNAME.github.io` |

Replace `YOUR-USERNAME` with your actual GitHub username. Just `username.github.io` — no `https://`, no path, no trailing slash. Remove any conflicting A or CNAME records on `@` or `www` that were there by default (parking pages, etc.).

### Step 4. Wait, then enable HTTPS
DNS propagation takes anywhere from a few minutes to a few hours (occasionally 24h). Once it works:
1. Go back to **Settings → Pages** on your repo.
2. You'll see "DNS check successful" next to your domain.
3. Check the box **Enforce HTTPS**. GitHub provisions a free SSL cert automatically.
4. Site is now on `https://hername.com`. 🎉

### Troubleshooting
- **"Domain does not resolve to the GitHub Pages server"** — DNS hasn't propagated yet. Wait longer, or double-check the A records are typed exactly.
- **Site works on `www.hername.com` but not `hername.com`** — the four A records on `@` are missing or wrong.
- **"Enforce HTTPS" checkbox is grayed out** — GitHub needs DNS to fully resolve before issuing a cert. Usually works within an hour of DNS being correct.

---

## 🧪 Good-to-know tips

- **No database, no server, no login.** The whole site is just files. It can never break from a backend outage, and hosting is effectively free forever.
- **Contact form?** The current setup is a plain `mailto:` link. If you want a real form later, services like [Formspree](https://formspree.io/) or [Web3Forms](https://web3forms.com/) drop in with ~3 lines of HTML, no backend needed.
- **Renaming a nav item?** The navigation is duplicated at the top of each page. If you rename "Short Films" → "Films", update it on every `.html` file. Five finds-and-replaces.
- **Font not loading?** Keep the `<link href="https://fonts.googleapis.com/..."` tag inside the `<head>` of each HTML file — that pulls in Fraunces + Instrument Sans from Google Fonts.
- **SVG placeholders look odd?** They're intentional — soft monochrome gradients that look like abstract editorial imagery. They make the site look complete before real photos exist. Replace them any time.

---

Good luck, and congrats on being the kind of partner who builds their writer a website.
