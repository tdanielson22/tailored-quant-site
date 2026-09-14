# consultancy-site

A minimal Jekyll site (Minimal Mistakes theme) with:
- `/bio/` — about you
- `/samples/` — sample project writeups
- `/demo/` — a live, in-browser Python model via Pyodide (no download, no server)
- `/writing/` — blog posts, with a spot to embed a Buttondown/Substack signup form
- `/contact/` — email link, with commented-out real form options

## 1. Try it locally (optional but recommended)

Requires Ruby installed.

```
bundle install
bundle exec jekyll serve
```

Visit `http://localhost:4000`. Edit any `.md` file and the page reloads.

## 2. Put it on GitHub

```
git init
git add .
git commit -m "initial site"
```

Create a new repo on GitHub named `yourusername.github.io` (this exact
naming makes GitHub Pages serve it at the root of that GitHub subdomain,
which you'll then point your real domain at — see step 4). Push:

```
git remote add origin https://github.com/yourusername/yourusername.github.io.git
git branch -M main
git push -u origin main
```

## 3. Turn on GitHub Pages

In the repo: Settings > Pages > Build and deployment > Source: "Deploy from
a branch" > Branch: `main` / root. Save. Give it a couple minutes — your
site will be live at `https://yourusername.github.io`.

## 4. Point your GoDaddy domain at it

Two DNS records at GoDaddy (DNS Management for your domain):

**A records** (for the apex/root domain, e.g. `yourdomain.com`) — add four
A records all pointing to GitHub's IPs:
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**CNAME record** (for `www.yourdomain.com`) pointing to:
```
yourusername.github.io
```

Then in your repo, add a file named `CNAME` (no extension) at the root
containing just your domain:
```
www.yourdomain.com
```

Also update `_config.yml`'s `url:` field to match. DNS changes can take a
few minutes to 48 hours to propagate. GitHub will auto-issue an HTTPS
certificate once it detects the domain is correctly pointed — check the
"Enforce HTTPS" box in Settings > Pages once it's available.

## 5. Editing content

- Bio/samples/contact/demo text: edit the `.md` files in `_pages/`.
- New blog post: add a file to `_posts/` named `YYYY-MM-DD-title.md` with
  the same front matter pattern as the example post.
- Nav bar order/labels: `_data/navigation.yml`.
- Site title, author info, social links: `_config.yml`.

## 6. Adding more interactive Pyodide demos

Duplicate `_pages/demo.md`, give it a new `permalink:`, and add it to
`_data/navigation.yml`. Keep the Python model logic in the
`pyodide.runPythonAsync(...)` block and wire your own HTML inputs to it —
the pattern in the existing demo (sliders -> JS event listener -> call into
Python -> update a result div) generalizes to most simple models. For
models needing numpy/pandas/etc., load them first:

```js
await pyodide.loadPackage(["numpy", "pandas"]);
```

## 7. Email list (optional)

If you go with Buttondown or Substack for the writing/email side, both give
you a simple embeddable signup form — drop the snippet into `_pages/writing.md`
where indicated by the HTML comment. This keeps posts and signup together
even if the actual email sending happens on their platform.
