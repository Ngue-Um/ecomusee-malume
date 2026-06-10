# How to Update the Écomusée de Malumé Website on GitHub

**Repository:** https://github.com/Ngue-Um/ecomusee-malume  
**Live website URL:** https://ngue-um.github.io/ecomusee-malume/

---

## What goes into the repository

Use the contents of the **`website-clean`** folder — it contains only what the website needs:

```
website-clean/
├── index.html                  ← The website (single page, bilingual EN/FR)
├── GITHUB-UPDATE-GUIDE.md      ← This guide
└── assets/
    └── images/
        ├── logo.png
        ├── hero-bg.jpg
        ├── about-bridge.jpg
        ├── president.jpg
        ├── colonial/           ← 3 archive photographs
        └── gallery/            ← 25 web-optimised photographs
```

Total size: ~17 MB. Everything else (raw photos, videos, PDF documents) should stay on your computer only — do not put them in the GitHub repository.

---

## Step 1 — Install Git (if not already installed)

**Mac:** Open Terminal and type `git --version`. If Git is not installed, macOS will prompt you to install it automatically.  
**Windows:** Download from https://git-scm.com/download/win and run the installer.

---

## Step 2 — First-time setup: clone the repository

Open **Terminal** (Mac) or **Git Bash** (Windows) and run:

```bash
git clone https://github.com/Ngue-Um/ecomusee-malume.git
cd ecomusee-malume
```

This downloads the repository to a folder called `ecomusee-malume` on your computer. You only need to do this once.

---

## Step 3 — Copy the website files into the repo folder

In Finder (Mac) or File Explorer (Windows):

1. Open the `ecomusee-malume` folder you just cloned
2. Delete everything inside it **except the hidden `.git` folder** (you won't see it by default — it is invisible and must not be touched)
3. Copy the contents of `website-clean` into the `ecomusee-malume` folder: `index.html`, `assets/`, and `GITHUB-UPDATE-GUIDE.md`

---

## Step 4 — Commit and push

In Terminal, from inside the `ecomusee-malume` folder:

```bash
git add .
git commit -m "Update website"
git push origin main
```

If Terminal asks for your GitHub credentials, enter your GitHub **username** and a **Personal Access Token** as the password (GitHub no longer accepts your account password here — see Step 5 if you need to create one).

---

## Step 5 — Create a Personal Access Token (if needed)

1. Go to https://github.com and sign in
2. Click your profile photo in the top-right corner → **Settings**

   > Settings is reached via your **profile photo menu**, not from inside the repository.

3. In the left sidebar that appears, scroll all the way down and click **Developer settings**
4. Click **Personal access tokens** → **Tokens (classic)**
5. Click **Generate new token (classic)**
6. Give it a name (e.g. "ecomusee push"), set expiration to 90 days, tick the **repo** checkbox
7. Click **Generate token** and copy it immediately — you will not see it again
8. Use this token as your password when Terminal asks during `git push`

---

## Step 6 — Enable GitHub Pages (first time only)

This makes the website publicly accessible at `https://ngue-um.github.io/ecomusee-malume/`.

1. Go to https://github.com/Ngue-Um/ecomusee-malume in your browser
2. Look at the row of tabs just below the repository name: **Code · Issues · Pull requests · Actions · Projects · Wiki · Security · Insights · Settings**
3. Click the **Settings** tab (last one on the right)
4. In the left sidebar of the Settings page, scroll down and click **Pages**
5. Under **Build and deployment**, set:
   - Source: **Deploy from a branch**
   - Branch: **main**
   - Folder: **/ (root)**
6. Click **Save**

Your site will be live within 1–3 minutes. You can check its status under the **Actions** tab.

---

## Making future updates

### The golden rule
Every update follows the same three-step pattern:
1. **Change the file(s)** — copy images into the right folder and/or edit `index.html`
2. **Commit** — tell Git what changed and give it a short label
3. **Push** — send the commit to GitHub; the site updates within 1–3 minutes

---

### To update text content
1. Open `index.html` in any text editor (TextEdit on Mac, Notepad on Windows, or VS Code)
2. Use **Cmd+F** (Mac) or **Ctrl+F** (Windows) to search for the text you want to change
3. Edit and save
4. In Terminal, from inside `ecomusee-malume/`:
   ```bash
   git add index.html
   git commit -m "Update text"
   git push origin main
   ```

---

### To add or replace a board member's photo
1. Crop and save the photo as a `.jpg` or `.jpeg`, named with the person's name in lowercase with hyphens (e.g. `bikoe-julienne.jpg`). Keep it under 500 KB.
2. Copy it into `ecomusee-malume/assets/images/`
3. Open `index.html` and search for the person's name. Add this line **inside their board card**, just above the `<div class="board-role">` line:
   ```html
   <img src="assets/images/bikoe-julienne.jpg" alt="Mme Julienne Bikoe" class="president-photo"
        onerror="this.style.display='none'" />
   ```
   If they already have a photo, just replace the old file with the new one — no HTML change needed.
4. Save, then in Terminal:
   ```bash
   git add assets/images/bikoe-julienne.jpg index.html
   git commit -m "Add photo: Bikoe Julienne"
   git push origin main
   ```

> **Important:** file names are case-sensitive on GitHub Pages. Use lowercase only. `Bikoe.jpg` and `bikoe.jpg` are treated as different files.

---

### To add a new gallery photo
1. Resize the photo to no wider than **1600px** and save as a `.jpg`, under 1 MB. Use a clear lowercase name (e.g. `chutes-libam-02.jpg`).
2. Copy it into `ecomusee-malume/assets/images/gallery/`
3. Open `index.html`, search for `const GALLERY`, scroll to the end of the list (just before `];`) and add:
   ```javascript
   { src:'assets/images/gallery/chutes-libam-02.jpg',
     en:'Caption in English',
     fr:'Légende en français' },
   ```
   Add `wide:true` after the `fr:` value for a landscape photo you want displayed across two columns.
4. Save, then in Terminal:
   ```bash
   git add assets/images/gallery/chutes-libam-02.jpg index.html
   git commit -m "Add gallery photo: chutes-libam-02"
   git push origin main
   ```

---

### To add a new video testimony
1. Upload the video to Google Drive and set sharing to **"Anyone with the link → Viewer"**
2. Copy the file ID from the URL: `drive.google.com/file/d/`**FILE_ID**`/view`
3. Open `index.html`, search for `testimony-wrap`, and duplicate the `<div class="video-card">` block, replacing the file ID in the `src` attribute with your new one
4. Update the caption labels (`data-en` and `data-fr`) inside that block
5. Save, then in Terminal:
   ```bash
   git add index.html
   git commit -m "Add video testimony: [name/location]"
   git push origin main
   ```

---

## Troubleshooting

| Problem | Solution |
|---|---|
| `git push` asks for a password | Use your Personal Access Token, not your GitHub account password (see Step 5) |
| Cannot find the Settings tab | Make sure you are on the repository page at github.com/Ngue-Um/ecomusee-malume, not on your profile page |
| Pages option not visible in Settings | Scroll down in the left sidebar — Pages is below the General and Code sections |
| Site not updating after push | Wait 2–3 minutes; check the **Actions** tab for build status |
| Images not showing on the live site | File names are case-sensitive on GitHub Pages — `Gallery-01.jpg` and `gallery-01.jpg` are different files |
| `git push` is very slow | The repo may contain large files; make sure only `website-clean` contents are being pushed |
