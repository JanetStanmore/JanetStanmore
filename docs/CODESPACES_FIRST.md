# Codespaces-First Workflow (No Local Setup)

This guide is for your preferred flow: **upload to GitHub first, then run only in Codespaces**.

## 1) Upload repository to GitHub from this environment
If your repository is already on GitHub, skip to step 2.

### Using GitHub CLI
```bash
git init
git add .
git commit -m "Initial commit: Instant Music Lab"
gh auth login
gh repo create instant-music-lab --public --source=. --remote=origin --push
```

### If `gh` is unavailable
1. Create an empty repo on github.com.
2. Push manually:
```bash
git init
git add .
git commit -m "Initial commit: Instant Music Lab"
git remote add origin https://github.com/<username>/instant-music-lab.git
git branch -M main
git push -u origin main
```

## 2) Open in Codespaces
1. Go to your GitHub repo.
2. Click **Code** → **Codespaces** → **Create codespace on main**.
3. Wait for container setup (`.devcontainer/devcontainer.json`).

## 3) Configure environment secrets in Codespaces
Create `.env.local` in the root:
```bash
cp .env.example .env.local
```
Set:
- `SUPABASE_URL`
- `SUPABASE_SERVICE_ROLE_KEY`

## 4) Setup database (Supabase)
1. Open Supabase SQL editor.
2. Run `supabase/schema.sql`.

## 5) Run web app in Codespaces
```bash
npm install
npm run dev
```
Then open forwarded port 3000.

## 6) (Optional) Run mobile from Codespaces
```bash
cd mobile
npm install
npm run start
```
Use Expo tunnel/QR flow if needed.

## 7) Daily workflow
```bash
git checkout -b feature/my-change
# edit files
npm run typecheck
npm run lint
git add .
git commit -m "feat: ..."
git push -u origin feature/my-change
```
Create PR on GitHub.
