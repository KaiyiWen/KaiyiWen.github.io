# www.kaiyiwen.com

Personal academic website — plain HTML + CSS, no build step, no dependencies.
Served by GitHub Pages from the `main` branch of `KaiyiWen/KaiyiWen.github.io`.

## Files

| File | What it is |
|---|---|
| `index.html` | The entire site. All content lives here. |
| `style.css` | All styling. |
| `assets/` | CV, paper PDFs, teaching evaluation, photo. |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is. |
| `CNAME` | Custom domain. **Only add this at DNS cutover time** (see below). |

## How to update

### Add a working paper

1. Drop the PDF in `assets/` (lowercase, hyphens, e.g. `my-new-paper.pdf`).
2. Copy an existing `<div class="paper">…</div>` block in `index.html` and edit it:
   - `.t` — title, linked to the PDF
   - `.m` — coauthors, then `<span class="status">` for the status line
   - `<details>` — the abstract, and optionally a `<p class="venues">` list of presentations
3. Commit and push. GitHub Pages redeploys in ~1 minute.

### Change a paper's status

Edit the text inside `<span class="status">…</span>`. Examples used on the site:
`Working paper` · `Under review` · `Submitted` · `Minor revision (second round), <em>Land Economics</em>`

### Move a paper to Publications

Cut the `<div class="paper">` block into the `<h3>Publications</h3>` group, replace the
PDF link with the DOI, and drop the `<details>` block.

### Update the CV

Replace `assets/cv.pdf`. The filename must stay the same — nothing else needs editing.

## Preview locally

```bash
cd ~/my-todo/KaiyiWen.github.io && python3 -m http.server 4321
```

Then open <http://localhost:4321>.

## Custom domain (www.kaiyiwen.com)

Not connected yet. When ready:

1. At the DNS provider, add for the apex `kaiyiwen.com`:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` (A records)
2. Add a CNAME record: `www` → `kaiyiwen.github.io`
3. Create a file named `CNAME` in this repo containing exactly: `www.kaiyiwen.com`
4. In the repo's Settings → Pages, set the custom domain and tick **Enforce HTTPS**
5. Only after the new site loads at www.kaiyiwen.com over HTTPS, cancel the Wix plan.
