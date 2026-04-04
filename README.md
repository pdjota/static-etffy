# static-etffy

Static site for etffy, deployed separately from the Django tracker.

Generated files live in **`public/`** (Vercel `outputDirectory`). Rebuild them from the Django app:

```bash
cd ..   # etffy project root (parent of static-etffy)
python manage.py export_public_html
```

Options:

- `--only-latest` — only `public/index.html` and `public/hsbc_report/index.html` (no `report/<date>/` trees).
- `--out /other/path` — custom output directory.

This uses Django’s **test `Client`**, so you get the same HTML as `runserver` without starting a port. To mirror a live server:

```bash
# from etffy root
python manage.py runserver 0.0.0.0:8000
# then curl http://127.0.0.1:8000/ …
```

## GitHub

From this directory:

```bash
git init
git add .
git commit -m "Initial static-etffy"
```

Create a new empty repository on GitHub (e.g. `static-etffy`), then:

```bash
git remote add origin https://github.com/<your-org>/static-etffy.git
git branch -M main
git push -u origin main
```

### Parent repo + subfolder

If the parent `etffy` repo should not include this site, add to the parent `.gitignore`:

```
static-etffy/
```

Then keep `static-etffy` as its own git root (nested repo). Alternatively:

- **Submodule** (parent tracks a commit of this repo):

  ```bash
  cd ..
  git submodule add https://github.com/<your-org>/static-etffy.git static-etffy
  ```

## Vercel

1. In [Vercel](https://vercel.com), **Add New → Project** and **Import** the GitHub repo.
2. **Root Directory**: leave `.` (repository root is this project).
3. **Framework Preset**: Other (static). **Output directory**: `public` (see `vercel.json`).
4. Deploy.

CLI (optional):

```bash
npm i -g vercel
cd static-etffy
vercel
```

Site root is **`public/`** (e.g. `public/index.html` → `/`).
