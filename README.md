# ayoubg1.dev

My personal site — projects, writing, and socials. Plain HTML + CSS, no build step.

## File structure

```
ayoubg1.dev/
├── index.html          ← main page (hero, about, projects, blog list, contact)
├── style.css           ← all styles
├── CNAME               ← tells GitHub Pages to serve at ayoubg1.dev
├── posts/
│   └── hello-world.html
└── README.md
```

## What to edit (search-and-replace these)

In `index.html`:

- `[your city]` → where you live
- `[what you're working on]` → current focus
- `[a technology]`, `[a project]`, `[a hobby]` → about section blanks
- **Project cards** (3 of them) → replace title, description, tags, and links
- **Writing list** → 3 placeholder posts to replace as you write more
- **Socials** → `@ayoubg1` handles and `hello@ayoubg1.dev` email
- **Stack list** in the About card → your real stack

In `posts/hello-world.html`:

- Rewrite the body, change the date in two places (the `<time>` tag and the visible text).

To add a new post: copy `posts/hello-world.html`, give it a new filename, edit content, and add a new `<li class="post">` to the writing list in `index.html`.

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

After a minute you'll see your site live at `https://ayoubg1.github.io`.

### 3. Connect the custom domain

The `CNAME` file in this repo already contains `ayoubg1.dev`, so GitHub will recognize the domain automatically.

At your domain registrar (where you bought `ayoubg1.dev`), add these DNS records:

**For the apex domain (`ayoubg1.dev`)** — four `A` records pointing to GitHub:

| Type | Name | Value           |
| ---- | ---- | --------------- |
| A    | @    | 185.199.108.153 |
| A    | @    | 185.199.109.153 |
| A    | @    | 185.199.110.153 |
| A    | @    | 185.199.111.153 |

**For `www.ayoubg1.dev`** — one `CNAME` record:

| Type  | Name | Value                  |
| ----- | ---- | ---------------------- |
| CNAME | www  | ayoubg1.github.io.     |

DNS propagation takes anywhere from a few minutes to a few hours.

### 4. Enable HTTPS

Back on **Settings → Pages**, once DNS is verified (green check), tick **Enforce HTTPS**. GitHub will issue a free Let's Encrypt certificate. Done.

## Local preview

Just open `index.html` in your browser, or run:

```bash
python3 -m http.server 8000
```

then visit http://localhost:8000.

## Putting it on your CV

Once it's live, you can list it as:

> **Portfolio:** ayoubg1.dev

That's it. Have fun.
