# NeetCode 150 Flashcards — PWA Setup Guide

## Files in this folder
```
flashcard-pwa/
├── index.html        ← The entire app (all cards, all logic)
├── manifest.json     ← Makes it installable as an app
├── sw.js             ← Service worker (enables offline use)
└── icons/
    ├── icon-192.png
    ├── icon-512.png
    ├── apple-touch-icon.png  ← What appears on iPhone home screen
    └── favicon.png
```

---

## Step 1 — Test locally on your Mac

Open Terminal and run:
```bash
cd ~/Desktop/flashcard-pwa   # wherever you put this folder
python3 -m http.server 8080
```
Then open http://localhost:8080 in your browser. You should see the app.

---

## Step 2 — Put it on GitHub (so your phone can access it)

### First time only — create a GitHub account
Go to https://github.com and sign up (free).

### Install Git if you don't have it
```bash
git --version   # if this works, you have it
# If not: brew install git
```

### Create a new repo on GitHub
1. Go to https://github.com/new
2. Name it: `leetcode-flashcards`
3. Set to **Public**
4. Click "Create repository"

### Push your files
```bash
cd ~/Desktop/flashcard-pwa

git init
git add .
git commit -m "Initial flashcard app"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/leetcode-flashcards.git
git push -u origin main
```
(Replace YOUR_USERNAME with your GitHub username)

### Enable GitHub Pages
1. Go to your repo on GitHub
2. Click **Settings** → **Pages**
3. Under "Source" select **Deploy from branch**
4. Choose **main** branch, **/ (root)** folder
5. Click **Save**

Wait ~60 seconds. Your app will be live at:
`https://YOUR_USERNAME.github.io/leetcode-flashcards`

---

## Step 3 — Install on your iPhone

1. Open Safari on your iPhone (must be Safari, not Chrome)
2. Go to `https://YOUR_USERNAME.github.io/leetcode-flashcards`
3. Tap the **Share button** (box with arrow pointing up)
4. Scroll down and tap **"Add to Home Screen"**
5. Tap **Add**

Done! You now have an app icon on your home screen. Tap it — it opens fullscreen with no browser chrome, just like a real app.

---

## Step 4 — Updating the app (your daily workflow)

Whenever you edit `index.html` on your Mac:
```bash
cd ~/Desktop/flashcard-pwa
git add .
git commit -m "Add system design cards"
git push
```

Your phone will get the update automatically the next time it opens the app with internet. (Offline it uses the cached version.)

---

## Notes
- Works fully offline after first load (service worker caches everything)
- Your mastery ratings are saved in memory per session (we can add persistent storage later)
- To add more cards: edit the CARDS array in index.html
