# n0mchem.com

**1,000 Grade 11 chemistry nomenclature questions. One page. Black & white. Zero dependencies.**

![Static](https://img.shields.io/badge/site-static-black)
![HTML5](https://img.shields.io/badge/html5-single_file-white)
![Questions](https://img.shields.io/badge/questions-1000-white)
![Dependencies](https://img.shields.io/badge/dependencies-0-black)
![License](https://img.shields.io/badge/license-MIT-white)

n0mchem.com is a single-page drill site for the **Grade 11 Chemistry Nomenclature Quiz** — binary molecular and ionic compounds, Stock vs. Classical naming, polyatomic ions and oxyanions, acids and bases, peroxides and hydrates, and organic nomenclature. Every question ships with an explanation, so a wrong answer is a study moment, not a dead end.

> **Live demo:** `https://lettermantest.github.io/n0mchem.github.io/`

---

## Table of Contents

- [Features](#features)
- [Question Coverage](#question-coverage)
- [Quick Start](#quick-start)
- [Deploy to GitHub Pages](#deploy-to-github-pages)
- [Custom Domain](#custom-domain)
- [Project Structure](#project-structure)
- [How It Works](#how-it-works)
- [Customizing](#customizing)
- [Contributing](#contributing)
- [License](#license)

---

## Features

| Feature | Details |
|---|---|
| **1,000 questions** | Embedded directly in the page — works offline once loaded |
| **One question at a time** | Random order, no repeats until the deck cycles |
| **Submit-to-answer flow** | Pick an option, hit Submit — explanation appears only after answering |
| **Skip support** | Skip any question; skips are counted and the question returns later |
| **Instant explanations** | Every question has a rule recap, right or wrong |
| **Progress tracking** | Answered / correct / accuracy / skipped, with a progress bar |
| **Persistent session** | Scores survive reloads via `localStorage` (`n0mchem-v2`) |
| **Built-in study material** | Collapsible cheat sheet: prefixes, Classical table, oxyanion ladder, acid mapping, alkane table, ring/benzene rules |
| **Black & white design** | Pure monochrome, rounded cards, mobile-friendly, no frameworks |
| **Zero dependencies** | No CDNs, no fonts, no tracking, no build step — one HTML file |

---

## Question Coverage

| # | Topic | Questions | What's drilled |
|---|---|---|---|
| 1 | Binary Molecular | 150 | Prefixes, no `mono-` on element 1, oxygen vowel-drop, halogen–oxygen order, diatomics (`Cl₂` = chlorine gas), common names (ammonia, water, methane…) |
| 2 | Binary Ionic | 100 | Metal + `-ide`, criss-cross with lowest-ratio reduction, both directions |
| 3 | Multivalent Ionic | 150 | Stock (Roman numerals) ↔ Classical (`-ous`/`-ic`), Hg₂²⁺ exception, formative-quiz key items |
| 4 | Polyatomic Ions | 150 | Oxyanion ladder (`per-ate` / `-ate` / `-ite` / `hypo-ite`), `NH₄⁺` / `OH⁻` / acetate, hydrogen polyatomics, `bi-` rule |
| 5 | Acids & Bases | 150 | Bases as cation + `OH⁻`, binary `hydro-…-ic` acids, `(aq)` vs `(g)`, oxyacid suffix mapping |
| 6 | Peroxides & Hydrates | 100 | `O₂²⁻` never reduced, hydrate `prefix-hydrate` naming, anhydrous vs. water of hydration |
| 7 | Organic | 200 | `CₙH₂ₙ₊₂` alkanes, longest-chain / lowest-locant / alphabetical branching, `-ene` / `-yne` priority, `cyclo-` rings, benzene substitution |
| | **Total** | **1,000** | |

---

## Quick Start

No tooling required. Any static server (or even `file://`) works.

```bash
# Clone and open
git clone https://github.com/lettermantest/n0mchem.github.io.git
cd n0mchem.github.io
open index.html          # or double-click it
```

Serve locally (recommended — matches Pages behavior):

```bash
# Python 3
python -m http.server 8000
# then visit http://localhost:8000
```

Resetting progress: use the **Reset score** button on the page, or clear the `n0mchem-v2` key in browser storage.

---

## Deploy to GitHub Pages

Only two files are needed: **`index.html`** and **`.nojekyll`**.

**Via the web UI (fastest):**

1. Create a new public repo (e.g. `n0mchem`).
2. Upload `index.html` and `.nojekyll` to the repo root.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set Source to **Deploy from a branch**, Branch to **`main`** and folder to **`/ (root)`**. Save.
5. Your site goes live at `https://lettermantest.github.io/n0mchem.github.io/` within a minute or two.

**Via the command line:**

```bash
git init
git add index.html .nojekyll README.md
git commit -m "Launch n0mchem.com — 1000 nomenclature questions"
git branch -M main
git remote add origin https://github.com/lettermantest/n0mchem.github.io.git
git push -u origin main
# Then enable Pages as in steps 3–5 above.
```

## Custom Domain

To serve the site from `n0mchem.com`:

1. Add a file named `CNAME` in the repo root containing exactly:
   ```
   n0mchem.com
   ```
2. In your DNS provider, point the apex to GitHub Pages (`185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`) or use a `www` CNAME to `lettermantest.github.io`.
3. In **Settings → Pages**, enter the custom domain and check **Enforce HTTPS**.

---

## Project Structure

```
.
├── index.html   # The entire site — markup, styles, JS, all 1,000 questions
├── .nojekyll    # Tells Pages to skip Jekyll processing
├── README.md    # This file
└── LICENSE      # MIT license
```

---

## How It Works

- **Single file.** `index.html` contains everything: CSS, JavaScript, and the full question array. No network requests are made after load.
- **Random deck.** On load, question indices are Fisher–Yates shuffled. Submit advances the deck; exhausting it reshuffles.
- **Answer flow.** Options are selectable but inert until **Submit** is pressed. The selection is then graded, the explanation revealed, and the result stored.
- **Scoring.** `answered: { questionId: { pick, correct } }` plus a skip counter persist under the `n0mchem-v2` localStorage key.
- **Study material.** A static, collapsible reference section covers every rule on the quiz — usable with or without attempting questions.

---

## Customizing

| Goal | Where |
|---|---|
| Change styling / rounding / theme | `<style>` block in `index.html` |
| Edit study material | `<details class="material">` section in `index.html` |
| Edit questions or explanations | `QUESTIONS` array in the `<script>` block in `index.html` |

---

## Contributing

Issues and pull requests are welcome:

1. Fork the repo and create a feature branch (`git checkout -b fix/oxyacid-typo`).
2. Make your correction directly in `index.html` (questions live in the `QUESTIONS` array).
3. Open a PR with a clear description of the correction.

---

## License

MIT — see [LICENSE](LICENSE). Study hard.
