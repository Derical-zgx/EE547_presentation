# FPS-MetaSync — Presentation Deck (HTML / reveal.js)

A black-and-red, Valorant-styled HTML presentation for **Esport Analyse System**. This version preserves the original **32-slide** structure and updates the content from the latest PDF.

## Quick start

```bash
python -m http.server 8000
```

Open:

```text
http://localhost:8000/
```

## Presenting

| Key | What it does |
| --- | --- |
| → / Space | Next slide |
| ← | Previous slide |
| S | Speaker view |
| F / F11 | Full-screen |
| ESC / O | Overview |
| B / . | Black screen |

## File layout

```text
.
├── index.html
├── css/
│   └── valorant.css
└── README.md
```

## Export to PDF

Open:

```text
http://localhost:8000/?print-pdf
```

Then use browser Print → Save as PDF, Landscape, Margins None, Background graphics ON.
