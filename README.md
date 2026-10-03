# SplitRoom — Real-Time Room Expense Tracker

Static site (one `index.html`) + Firebase Firestore for real-time sync. No build step.

## 1. Firebase (free Spark plan)
1. https://console.firebase.google.com → **Add project**.
2. **Build → Firestore Database → Create database** (any region, production mode).
3. **Rules** tab → paste the contents of `firestore.rules` → **Publish**.
4. **Project settings (gear) → Your apps → Web (`</>`)** → register an app → copy the `firebaseConfig` values.
5. Open `index.html`, find `FIREBASE_CONFIG` near the top of the script and paste your values.
   (These web keys are not secrets; the rules are what protect your data.)

## 2. GitHub
```
git init && git add . && git commit -m "SplitRoom"
git branch -M main
git remote add origin https://github.com/<you>/splitroom.git
git push -u origin main
```

## 3. Vercel
Vercel → **Add New → Project** → import the repo → Framework Preset **Other**, leave Build/Output empty → **Deploy**.
Every push to `main` redeploys automatically.

## Using it
Create a room, copy the invite link (`https://your-app.vercel.app/#RM-XXXXXXXXXX`), send it to roommates. Each person picks their name and they're in. The app remembers your room on that device.

## Security note
Anyone who has a Room ID can read and edit that room (IDs are 10 random characters, so they can't be guessed or listed). Don't treat it as bank-grade; for stricter control, add Firebase Anonymous Auth and tighten `firestore.rules`.
