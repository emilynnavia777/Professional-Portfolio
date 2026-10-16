# Connecting this website to GitHub

Your repository is **already initialised and committed** — 2 commits, 5 tracked files,
clean working tree. You only need to create the GitHub repo and push.

---

## Step 1 — Create a Personal Access Token (PAT)

GitHub no longer accepts account passwords for `git push`. You need a token.

1. Sign in to GitHub → click your **avatar** (top-right) → **Settings**
2. Scroll to the very bottom → **Developer settings**
3. **Personal access tokens** → **Tokens (classic)** → **Generate new token (classic)**
4. Configure:
   - **Note:** `physics-website-push`
   - **Expiration:** 90 days (or your preference)
   - **Scopes:** tick **`repo`** (the whole `repo` group — this allows creating and pushing to private repos)
5. Click **Generate token** and **copy it immediately** — GitHub shows it only once.

Direct link: <https://github.com/settings/tokens/new?scopes=repo&description=physics-website-push>

---

## Step 2 — Create an empty repository on GitHub

1. Go to <https://github.com/new>
2. **Repository name:** e.g. `physics-educator`
3. **Visibility:**
   - **Public** → required if you want free GitHub Pages hosting
   - **Private** → Pages needs a paid plan (Pro/Team/Enterprise)
4. **Important:** do **NOT** tick "Add a README", ".gitignore" or "license".
   The repo must be empty, or the push will be rejected and need a merge.
5. Click **Create repository**

---

## Step 3 — Push

Replace `YOUR-USERNAME` and `physics-educator` with your actual values:

```bash
cd /path/to/your/files

git remote add origin https://github.com/YOUR-USERNAME/physics-educator.git
git push -u origin main
```

When prompted:
- **Username:** your GitHub username
- **Password:** paste the **token** from Step 1 (not your password)

### Optional — store the token so you aren't asked every time

```bash
git config --global credential.helper store     # saves to ~/.git-credentials (plain text)
# or, safer:
git config --global credential.helper 'cache --timeout=3600'   # memory only, 1 hour
```

---

## Step 4 — Set your git identity (recommended)

The commits currently use a placeholder identity. To make them show as **you** on GitHub:

```bash
git config --global user.name  "Your Name"
git config --global user.email "your-github-email@users.noreply.github.com"
```

Find your noreply address at <https://github.com/settings/emails>.
Then rewrite the two existing commits (optional, only needed once):

```bash
git commit --amend --reset-author --no-edit
git push -f origin main
```

---

## Step 5 — Publish with GitHub Pages

A workflow is already included at `.github/workflows/deploy.yml`. It deploys automatically
on every push to `main`. To activate it:

1. In your repo → **Settings** → **Pages**
2. **Build and deployment → Source:** select **GitHub Actions**
3. Wait ~1 minute after pushing, then check the **Actions** tab for a green ✔
4. Your site is live at:

```
https://YOUR-USERNAME.github.io/physics-educator/
```

No Jekyll, bundler or `_config.yml` needed — it's a single static file.

---

## Repository contents

| File | Purpose |
| --- | --- |
| `index.html` | The entire website (~16 MB, all photos embedded as data URIs) |
| `README.md` | Project documentation |
| `.gitignore` | Excludes `uploads/`, `*.mp4`, `papers/*.pdf` |
| `papers/README.md` | Explains the past-paper archive filenames |
| `.github/workflows/deploy.yml` | Auto-deploys to GitHub Pages on push |

**Excluded on purpose:** the `uploads/` folder (48 original JPEGs, ~23 MB). The page never
references those files — every photo is embedded in `index.html` — so keeping them out makes
the repo ~12 MB instead of ~35 MB. They stay on disk as backups.

---

## Size notes

- `index.html` is **~16 MB**. GitHub's soft warning starts at 50 MB and the hard limit is
  100 MB per file, so you're comfortably within limits.
- GitHub Pages allows **1 GB** per site and **100 GB/month** bandwidth — plenty for a portfolio.
- First load takes a few seconds because of the embedded photos; afterwards the browser caches it.

---

## Adding the videos and past papers later

Both are optional and ignored by default. To publish them:

1. Put your files next to `index.html`:
   - `catapult.mp4`, `catapult2.mp4`, `electroscope.mp4`, `certificate.mp4`
   - `papers/hsc-physics-2019-past-paper.pdf` … through `2025`
2. Edit `.gitignore` and delete these two lines:
   ```
   *.mp4
   papers/*.pdf
   ```
3. Commit and push:
   ```bash
   git add -A
   git commit -m "Add videos and past papers"
   git push
   ```

Keep total repo size under 1 GB. If the videos are large, host them on YouTube or a
cloud drive instead and link out.

---

## Alternative — push without any command line

If you'd rather not use a terminal:

1. Install **GitHub Desktop** → <https://desktop.github.com/>
2. Sign in with your GitHub account
3. **File → Add Local Repository** → select the folder containing `index.html`
4. GitHub Desktop detects the existing repo and commits
5. Click **Publish repository** → choose name and visibility → **Publish**

---

## Alternative — drag-and-drop upload (simplest, no git)

Fine for a one-off, but you lose commit history and the auto-deploy workflow won't run
until you switch Pages back to "Deploy from a branch":

1. Create a new empty repo on GitHub
2. Click **uploading an existing file**
3. Drag in `index.html` and `README.md`
4. **Commit changes**
5. **Settings → Pages → Source: Deploy from a branch → main / root → Save**

---

## Troubleshooting

| Problem | Fix |
| --- | --- |
| `Authentication failed` | You used your password instead of the token, or the token lacks the `repo` scope |
| `Updates were rejected because the remote contains work` | You ticked "Add a README" when creating the repo. Run `git pull origin main --allow-unrelated-histories`, resolve, then push |
| `error: failed to push some refs` | Check the branch name: `git branch` should show `main` |
| Pages shows 404 | In **Settings → Pages**, confirm Source is **GitHub Actions**, and check the **Actions** tab for a failed run |
| Site loads but looks unstyled | Expected only if you edited the file and broke a tag — the shipped file parses cleanly |
