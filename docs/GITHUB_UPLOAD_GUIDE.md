# How to Run and Upload to GitHub

## A) Run Web App
```bash
npm install
cp .env.example .env.local
# fill SUPABASE_URL and SUPABASE_SERVICE_ROLE_KEY
npm run dev
```
Open `http://localhost:3000`.

## B) Run Mobile App
```bash
cd mobile
npm install
npm run start
```
Scan QR with Expo Go, or run emulator via `npm run android` / `npm run ios`.

## C) Create Supabase Table
- Open Supabase SQL Editor.
- Paste/run `supabase/schema.sql`.

## D) Upload to GitHub (new repo)
```bash
git init
git add .
git commit -m "Initial commit: Instant Music Lab web+mobile"
gh repo create instant-music-lab --public --source=. --remote=origin --push
```

## E) If `gh` CLI is not installed
1. Create empty repo manually on github.com.
2. Then run:
```bash
git remote add origin https://github.com/<your-user>/<repo>.git
git branch -M main
git push -u origin main
```
