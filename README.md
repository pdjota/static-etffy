# static-etffy

Static HTML site for ETF performance reports. Built files live in **`public/`** (Vercel `outputDirectory`, see `vercel.json`).

## Reports in `public/`

| URL path | File | What it is |
|----------|------|------------|
| `/` | `public/index.html` | **Home** — short intro and links to the three coverage sets. |
| `/report/` | `public/report/index.html` | **Broad universe** — rankings for the latest snapshot date (~thousands of ETFs from the screener). |
| `/report/<YYYY-MM-DD>/` | `public/report/<YYYY-MM-DD>/index.html` | Same **broad universe** report for one trading day. |
| `/hsbc_report/` | `public/hsbc_report/index.html` | **HSBC watchlist** — movers only for ETFs tied to the HSBC listed-fund watchlist for that run. |
| `/hsbc_report/<YYYY-MM-DD>/` | `public/hsbc_report/<YYYY-MM-DD>/index.html` | HSBC report for a specific date. |
| `/aviva_report/` | `public/aviva_report/index.html` | **Aviva watchlist** — movers only for ETFs tied to the Aviva listed-fund watchlist. |
| `/aviva_report/<YYYY-MM-DD>/` | `public/aviva_report/<YYYY-MM-DD>/index.html` | Aviva report for a specific date. |

Each report page shows top movers (e.g. top 10 / top 50 tables) from stored end-of-day snapshots. Actual HTML depends on whatever was last exported into `public/`.

## Deploy (Vercel)

1. In [Vercel](https://vercel.com), **Add New → Project** and import this repository.
2. **Root Directory**: `.` (repo root is this project).
3. **Framework Preset**: Other (static). **Output directory**: `public`.
4. Deploy.

CLI (optional):

```bash
npm i -g vercel
cd static-etffy
vercel
```

The live site serves **`public/`** (e.g. `public/index.html` → `/`).

## GitHub

From this directory:

```bash
git init
git add .
git commit -m "Initial static-etffy"
```

Create an empty repository, then:

```bash
git remote add origin https://github.com/<your-org>/static-etffy.git
git branch -M main
git push -u origin main
```

### Parent monorepo + subfolder

If a parent repo should not track this site, add to the parent `.gitignore`:

```
static-etffy/
```

Treat `static-etffy` as its own git root, or add it as a **submodule**:

```bash
cd ..
git submodule add https://github.com/<your-org>/static-etffy.git static-etffy
```
