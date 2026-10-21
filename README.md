# ayoubg1.dev

Personal site of Ayoub Dabbabi: projects, experience, writing and contact. Plain HTML + CSS, no build step.

## File structure

```
ayoubg1.dev/
├── index.html          ← main page (hero, about, projects, experience, writing, contact)
├── style.css           ← all styles
├── CNAME               ← tells GitHub Pages to serve at ayoubg1.dev
├── posts/
│   └── hello-world.html
└── README.md
```

## Editing content

All content lives in `index.html`; each section is marked with an HTML comment.

- **Hero**: intro text and the green "Open to Werkstudent roles" pill.
- **About**: three paragraphs plus the side cards (studying, stack, languages, currently).
- **Projects**: one `<article class="project">` per project, numbered `001`, `002`…
  Copy an existing one to add a new project.
- **Experience & Education**: one `<li class="tl-item">` per entry, newest first.
- **Writing**: one `<li class="post">` per post.
- **Contact**: one `<a class="social">` per link.

### Adding a YouTube video to a project

Videos use a click-to-load embed. The page shows the YouTube thumbnail and only loads
the player (from `youtube-nocookie.com`) when someone clicks it. That keeps the page fast
and avoids loading YouTube cookies until a visitor chooses to play, which matters for GDPR.

Take the video ID from the link (`https://youtu.be/VIDEO_ID`) and paste this block inside
the project's `<div class="project-main">`, replacing `VIDEO_ID` in all three places:

```html
<a class="yt" href="https://youtu.be/VIDEO_ID" data-id="VIDEO_ID" target="_blank" rel="noopener">
  <img src="https://i.ytimg.com/vi/VIDEO_ID/hqdefault.jpg" alt="Short description of the video" loading="lazy" />
  <span class="yt-icon" aria-hidden="true">▶</span>
  <span class="yt-note">Play video · loads from YouTube</span>
</a>
```

Without JavaScript, the thumbnail simply links to the video on YouTube.

### Adding a post

Copy `posts/hello-world.html`, give it a new filename, edit the content and the date
(both the `<time datetime>` attribute and the visible text), then add a new
`<li class="post">` to the Writing list in `index.html`.

## Deploy to GitHub Pages with the custom domain

### 1. Create the repo

Name it **`ayoubg1.github.io`** (it must match your GitHub username for the simplest setup). Make it public.

```bash
cd ayoubg1.dev
git init
git add .
git commit -m "initial site"
git branch -M main
git remote add origin https://github.com/ayoubg1/ayoubg1.github.io.git
git push -u origin main
```

### 2. Turn on Pages

In the repo on github.com → **Settings → Pages**:

- **Source**: Deploy from a branch
- **Branch**: `main` / `/ (root)`
- Save.

After a minute the site is live at `https://ayoubg1.github.io`.

### 3. Connect the custom domain

The `CNAME` file already contains `ayoubg1.dev`, so GitHub recognizes the domain automatically.

At your domain registrar, add these DNS records:

**Apex domain (`ayoubg1.dev`)**: four `A` records pointing to GitHub:

| Type | Name | Value           |
| ---- | ---- | --------------- |
| A    | @    | 185.199.108.153 |
| A    | @    | 185.199.109.153 |
| A    | @    | 185.199.110.153 |
| A    | @    | 185.199.111.153 |

**`www.ayoubg1.dev`**: one `CNAME` record:

| Type  | Name | Value               |
| ----- | ---- | ------------------- |
| CNAME | www  | ayoubg1.github.io.  |

DNS propagation takes anywhere from a few minutes to a few hours.

### 4. Enable HTTPS

Back on **Settings → Pages**, once DNS is verified (green check), tick **Enforce HTTPS**.
GitHub issues a free Let's Encrypt certificate.

## Local preview

Open `index.html` in your browser, or run:

```bash
python3 -m http.server 8000
```

then visit http://localhost:8000.
