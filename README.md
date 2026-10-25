# Vennela Manmohan — portfolio website

A plain static website (HTML, CSS and images — no build step, no framework).
It runs on any static host. These instructions use **GitHub** (free) to store it and
**Cloudflare Pages** (free) to serve it, with your own custom domain.

Total cost: **only the domain** (~$10–12/year). Hosting and the GitHub repo are free.

---

## What's in this folder

```
index.html        Home (hero + selected work)
about.html        About
servicenow.html   Case study — ServiceNow
vera.html         Case study — The Vera Circle
travalot.html     Case study — Travalot
habitnu.html      Case study — HabitNu
favicon.svg       The little "VM" browser-tab icon
images/           Every photo and screenshot the site uses
README.md         This file
```

Open `index.html` in a browser to preview it locally before you publish.

---

## Step 1 — Put the site on GitHub

1. Create a free account at **https://github.com** (this is the id + password you'll use
   to edit the site later).
2. Click the **+** (top-right) → **New repository**.
   - Repository name: `portfolio` (or anything).
   - Set it to **Public**.
   - Click **Create repository**.
3. On the new repo page, click **uploading an existing file**
   (the link reads: *"Get started by … uploading an existing file"*).
4. Add the files. **Important — the `images` folder:** GitHub's web page can't pick a
   folder with the "choose your files" button, and dragging a folder only works in
   **Google Chrome**. So either:
   - **In Chrome:** drag the six `.html` files + `favicon.svg` + `README.md` into the box,
     then drag the **`images` folder itself** (the folder, not the files inside it) into the
     box too. You'll see paths appear like `images/…`. Then Commit.
   - **Or (most reliable, any browser):** install the free **GitHub Desktop** app
     (desktop.github.com), copy all the unzipped files + the `images` folder into the repo
     folder, and click **Commit → Push**. Folders always upload correctly this way.
5. Click **Commit changes**.

> The `images/` folder must keep that exact name, and the pictures must stay inside it —
> that's what the pages point to. If images don't show on the live site, it's almost always
> because the `images` folder didn't finish uploading; re-upload it in Chrome or via GitHub Desktop.

---

## Step 2 — Publish it with Cloudflare Pages (free)

1. Create a free account at **https://dash.cloudflare.com**.
2. In the left menu: **Workers & Pages** → **Create** → **Pages** tab →
   **Connect to Git**.
3. Authorise GitHub, pick your `portfolio` repo, click **Begin setup**.
4. Build settings — leave them empty, this is a plain site:
   - Framework preset: **None**
   - Build command: **(leave blank)**
   - Build output directory: **`/`**
5. Click **Save and Deploy**. After ~30 seconds you'll get a live URL like
   `portfolio-xyz.pages.dev`. Your site is live.

Every time you change a file on GitHub, Cloudflare rebuilds the site automatically in
under a minute.

---

## Step 3 — Connect your own domain

1. Buy a domain. Cheapest with no markup: in Cloudflare, **Domain Registration →
   Register Domain**. (Any registrar works — Namecheap, Porkbun, etc.)
2. In your Pages project → **Custom domains** → **Set up a custom domain** → type your
   domain → **Continue** → **Activate domain**.
   - If you bought the domain **at Cloudflare**, DNS is set for you automatically.
   - If you bought it elsewhere, Cloudflare shows you the DNS records to add at your
     registrar (or move the domain's nameservers to Cloudflare). Follow the on-screen steps.
3. Give DNS a few minutes to an hour. HTTPS (the padlock) is turned on for you, free.

---

## How to edit text and images (signed in)

Everything is editable from GitHub in the browser — just sign in with your GitHub account.

### Edit text
1. Go to your repo on github.com and open the page you want, e.g. `about.html`.
2. Click the **pencil icon** (top-right of the file) to edit.
3. Find the text you want to change and type over it. The words sit between the tags,
   for example:
   `<h1 ...>I design clarity into software …</h1>` — change only the words, not the
   `<...>` parts around them.
4. Scroll down → **Commit changes**. The live site updates within a minute.

### Swap an image for a different picture
Every image has a filename like `images/871897c563a8…png`. To replace one:
1. Upload your new picture to the `images` folder **with the exact same filename** as the one
   you're replacing (Add file → Upload files). Keeping the same name means you don't touch any
   HTML. Commit.
2. Or upload it under a new name, then edit the page's `<img src="images/OLDNAME">` and change
   `OLDNAME` to your new filename.

### Adjust how an image looks (crop / zoom / resize / reposition)
You don't need an image editor for this — each adjustable image (every photo, folder cover
and the hero strip) has an **`ADJUST IMAGE`** comment in the HTML right above it, telling you
exactly what to change. Open the page, find the image, and edit the values on that image's line:

- **Reposition / crop — which part of the picture shows.** Change `object-position`:
  - `object-position: center` → centred (default)
  - `object-position: top` / `bottom` / `left` / `right` → pin to that edge
  - `object-position: 50% 30%` → fine control (first number = left↔right, second = top↔bottom)
  This is how you "crop" — the frame stays the same size and you slide the picture inside it.
- **Zoom in.** Add `transform: scale(1.2);` to the image's `style` (1.2 = 20% bigger; try
  1.1–1.4). Combine with `object-position` to zoom into a specific spot.
- **Resize the frame.** The picture sits in a box. Change that box's `aspect-ratio`
  (e.g. `aspect-ratio: 16 / 11` → try `4 / 3` or `1 / 1`) or its `height` to make the frame
  taller/shorter, or `max-width` to make it narrower.
- **The hero strip (home page).** Find the `ADJUST the hero strip` note: change `height: 304px`
  to show more or less of the strip, and `max-width` to make it wider or narrower.

For the big screenshots inside the case studies (shown full width), there's nothing to crop —
to make one smaller, add `max-width: 720px; margin: 0 auto;` to the `<div>` that wraps it.

> Tip: make one small change, commit, and check the live site before the next — that way you
> always know which edit did what.

### Add more "Off screen" photos (About page)
Open `about.html`, find the comment `<!-- PHOTOS -->`. Each photo is one
`<div class="drag" …>` block — copy one, paste it after the last, change the `left:`/`top:`
percentages, the `<img src>`, and the title/caption.

---

## A couple of things to fill in when you're ready

- **vera.html** has two placeholder numbers in square brackets — `[34]` (survey size) and
  `[18]` (first-week submissions). Replace them with the real figures, or reword the
  sentence, whenever you like.
- The **Résumé** links open an email asking for your résumé. If you'd rather link a PDF,
  upload `resume.pdf` to the repo and change the résumé links to `href="resume.pdf"`.
- Contact email (`vennelamanmohan@gmail.com`) and the **LinkedIn** URL appear in the
  footer of every page — search and replace if either changes.

That's it. Commit a change on GitHub, and your live site updates on its own.
