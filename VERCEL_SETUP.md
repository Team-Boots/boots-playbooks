# Deploying to Vercel (Native GitHub Integration)

No tokens, no secrets, no GitHub Actions workflow needed.
Vercel's GitHub App handles everything automatically once you connect the repository.

---

## One-time setup (≈ 2 minutes)

### Step 1 — Open the Vercel "Import" page

Go to: **https://vercel.com/new**

> If you are not logged in, sign in first at https://vercel.com/login

---

### Step 2 — Import your GitHub repository

1. Under **"Import Git Repository"**, click **"Continue with GitHub"** (if not already connected).
2. Find **`Team-Boots/boots-playbooks`** in the list and click **Import**.

> If the repo does not appear, click **"Adjust GitHub App Permissions"** and grant Vercel access to the `Team-Boots` organisation or the specific repo.

---

### Step 3 — Configure the project

Vercel will detect this is a static site automatically (thanks to `vercel.json`).

- **Framework Preset:** `Other`
- **Root Directory:** `.` (leave as-is)
- **Build Command:** *(leave blank)*
- **Output Directory:** `.` (leave as-is)

Click **Deploy**.

---

### Step 4 — Done ✅

Vercel will build and deploy the site immediately.
From this point on, **every push to `main` triggers a new production deployment automatically** — no extra configuration required.

Your stable production URL will be shown in the Vercel dashboard after the first deploy
(typically `https://boots-playbooks.vercel.app/` or a custom domain you configure).
Preview deployments get a unique URL per-commit (e.g. `https://boots-playbooks-<hash>.vercel.app/`).

---

## How it works

Vercel installs its **GitHub App** on the repository. The app receives a webhook event on every push, then Vercel pulls the code and deploys it. Nothing lives in GitHub Actions or GitHub Secrets.

| What you need | Token-based approach (old) | Native GitHub App (current) |
|---|---|---|
| `VERCEL_TOKEN` secret | ✅ required | ❌ not needed |
| `VERCEL_ORG_ID` secret | ✅ required | ❌ not needed |
| `VERCEL_PROJECT_ID` secret | ✅ required | ❌ not needed |
| GitHub Actions workflow | ✅ required | ❌ not needed |
| Vercel dashboard setup | one-time | one-time |

---

## Checking deployment status

- Open the repo on GitHub and look at the commit status dots — Vercel posts a check run on each commit.
- Or visit the **Vercel dashboard** at https://vercel.com/dashboard and open the `boots-playbooks` project.
