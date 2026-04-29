# FPS-MetaSync — Presentation Deck (HTML / reveal.js)

A black-and-red, Valorant-styled HTML presentation that mirrors the original
`Esport Analyse Sys.pptx` (32 slides). Built with [reveal.js 4.6](https://revealjs.com/)
and [Mermaid](https://mermaid.js.org/) for the architecture / timeline / user-flow diagrams.

The original PowerPoint file is **kept untouched** — this directory is a parallel,
browser-friendly version of the same deck.

---

## Quick start (local)

No build step. You only need a static file server because the page loads
reveal.js / Mermaid from a CDN.

### Option 1 — Python (already installed on your machine)

```powershell
cd presentation
python -m http.server 8000
```

Open <http://localhost:8000/> in Chrome / Edge / Firefox.

### Option 2 — Node (if you have it)

```powershell
cd presentation
npx --yes serve -p 8000 .
```

> First load fetches reveal.js + Mermaid from `cdn.jsdelivr.net`, so an internet
> connection is required the **first time**. After that, browser cache covers you
> for offline classroom use — open it once at home before the demo.

---

## Presenting in class

| Key                | What it does                                  |
| ------------------ | --------------------------------------------- |
| `→` / `Space`      | Next slide                                    |
| `←`                | Previous slide                                |
| `S`                | Open speaker view (notes + timer + next prev) |
| `F` / browser `F11`| Full-screen                                   |
| `ESC` / `O`        | Slide overview (thumbnails)                   |
| `B` / `.`          | Black / pause the screen                      |
| `?`                | Show help                                     |

### Connecting to the projector

1. Plug HDMI in.
2. Drag the browser window to the projector display, press **F11**.
3. On your laptop screen press **S** → speaker view (notes + clock + next slide).
4. Drive with the arrow keys. Use **B** to black out when you switch to a live
   demo (Flask SPA, K-means run, etc.).

---

## Hosting it online (optional but nice)

### GitHub Pages

```powershell
git add presentation
git commit -m "Add reveal.js deck"
git push
```

Then in the GitHub repo: **Settings → Pages → Deploy from branch → `main` /
`presentation`**. You'll get a public URL like
`https://<you>.github.io/<repo>/`.

### Vercel

```powershell
npx vercel deploy presentation --prod
```

### Export to PDF (backup for the demo)

reveal.js prints to PDF natively — handy as an offline fallback:

1. Open <http://localhost:8000/?print-pdf>
2. Browser **Print** → **Save as PDF**
3. Set *Layout: Landscape*, *Margins: None*, *Background graphics: ON*

---

## File layout

```text
presentation/
├── index.html          # all 32 slides
├── css/
│   └── valorant.css    # black-red Valorant theme (matches the SPA)
└── README.md           # this file
```

All assets except the local CSS come from CDN — there is nothing to install.

---

## Edit cheatsheet

* Each slide is one `<section>` element inside `.slides`.
* Section dividers use `class="divider"` and the title slide uses `class="title"`.
* For Valorant red emphasis, wrap text in `<em>...</em>` or
  `<span class="accent">...</span>`.
* Pills:
  `<span class="pill">…</span>`,
  `<span class="pill red">…</span>`,
  `<span class="pill green">DONE</span>`,
  `<span class="pill yellow">PARTIAL</span>`.
* Two-column layout: `<div class="grid-2">…</div>` (or `grid-2 lop` for 1.6 : 1).
* Cards: `<div class="card">…</div>` (or `card hot` for the red-glow variant).
* Mermaid diagrams: `<div class="mermaid">…flowchart code…</div>`.

---

## Suggested demo timing (≈ 18–20 min)

| Time   | Slides | What to do                                                           |
| ------ | ------ | -------------------------------------------------------------------- |
| 0–1 m  | 1–2    | Title + Project Summary                                              |
| 1–3 m  | 3–4    | Architecture text + diagram (linger on the Mermaid)                  |
| 3–5 m  | 5–8    | Background / Deployment / Timeline / References (move quickly)       |
| 5–9 m  | 9–14   | **Frontend** — switch to a tab with the live SPA running             |
| 9–13 m | 15–19  | Backend / data source / performance / DevOps                         |
| 13–16 m| 20–24  | **ML** — show a real `train_kmeans` run + `/api/clusters` JSON       |
| 16–18 m| 25–28  | API — optionally curl `/status` and `/api/matches?limit=3`           |
| 18–20 m| 29–32  | Conclusion + outcomes + descoped features → Q&A                      |
