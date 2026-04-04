# static-etffy

Static site for etffy, deployed separately from the Django tracker.

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
3. **Framework Preset**: Other (static). No install/build needed.
4. Deploy.

CLI (optional):

```bash
npm i -g vercel
cd static-etffy
vercel
```

Output: `index.html` at repo root is served as `/`.
