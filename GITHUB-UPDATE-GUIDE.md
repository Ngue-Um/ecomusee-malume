# How to Update the Écomusée de Malumé Website on GitHub

**Repository:** https://github.com/Ngue-Um/ecomusee-malume  
**GitHub Pages URL:** Once configured, your site will be at `https://ngue-um.github.io/ecomusee-malume/`

---

## What's in this folder

After the rebrand, the website folder contains:

```
Ecomusee-de-Malume-Website/
├── index.html              ← The main website (single page)
├── assets/
│   └── images/
│       ├── logo.png        ← Project logo
│       ├── hero-bg.jpg     ← Hero section background
│       ├── about-bridge.jpg
│       ├── njock-landscape.jpg
│       ├── gallery/        ← 8 curated gallery images
│       ├── ngoakntet/      ← Field photos
│       ├── photos/         ← Archive photos
│       ├── njock/
│       └── maps/
└── GITHUB-UPDATE-GUIDE.md  ← This file
```

---

## Step 1 — Install Git (if not already installed)

**Mac:** Git is pre-installed. Open Terminal and type `git --version` to confirm.  
**Windows:** Download from https://git-scm.com/download/win  
**Linux:** `sudo apt install git`

---

## Step 2 — Clone the repository (first time only)

Open **Terminal** (Mac/Linux) or **Git Bash** (Windows) and run:

```bash
git clone https://github.com/Ngue-Um/ecomusee-malume.git
cd ecomusee-malume
```

This creates a local copy of the repo on your computer.

---

## Step 3 — Copy the new website files into the repo

Copy **everything** from the `Ecomusee-de-Malume-Website` folder into the cloned repo folder:

```bash
# On Mac/Linux — adjust the source path to where your folder is:
cp -r /path/to/Ecomusee-de-Malume-Website/index.html .
cp -r /path/to/Ecomusee-de-Malume-Website/assets ./assets
```

Or simply drag-and-drop the files using Finder/Explorer into the `ecomusee-malume` folder.

> **Important:** The `assets/images/` folder contains the photos. These are large files.  
> If you want to keep the repo small, consider using [Git LFS](https://git-lfs.com/) for images (optional, see below).

---

## Step 4 — Stage and commit the changes

In Terminal, from inside the `ecomusee-malume` folder:

```bash
# See what changed
git status

# Stage all new/changed files
git add .

# Commit with a clear message
git commit -m "Rebrand: new website design with oral testimonies, gallery, and stakeholder content"
```

---

## Step 5 — Push to GitHub

```bash
git push origin main
```

If prompted, enter your GitHub username and a **Personal Access Token** (not your password).  
To create a token: GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic) → New token. Select `repo` scope.

---

## Step 6 — Enable GitHub Pages (first time only)

1. Go to https://github.com/Ngue-Um/ecomusee-malume
2. Click **Settings** → **Pages** (in the left sidebar)
3. Under **Source**, select: `Deploy from a branch`
4. Branch: `main` · Folder: `/ (root)`
5. Click **Save**

Your website will be live at:  
**https://ngue-um.github.io/ecomusee-malume/**  
(usually takes 1–2 minutes to deploy)

---

## Making future updates

### To update text content:
1. Open `index.html` in a text editor (TextEdit, VS Code, Notepad++)
2. Find the section you want to change (use Ctrl+F / Cmd+F to search)
3. Edit the text
4. Save, then repeat Steps 4–5 above

### To add new photos to the gallery:
1. Copy new `.jpg` files into `assets/images/gallery/`
2. In `index.html`, find the `actualImages` array (around line 370)
3. Add a new entry:
   ```javascript
   { path: 'assets/images/gallery/your-photo.jpg', alt: 'Description of photo' },
   ```
4. Save, commit, push

### To add a new video testimony:
1. Upload the video to Google Drive
2. Share it (Anyone with the link → Viewer)
3. Copy the file ID from the URL: `drive.google.com/file/d/FILE_ID_HERE/view`
4. In `index.html`, find the `<div class="testimony-grid">` section
5. Add a new `<div class="video-card">` block:
   ```html
   <div class="video-card">
     <iframe
       src="https://drive.google.com/file/d/YOUR_FILE_ID/preview"
       allow="autoplay" allowfullscreen
       title="Testimony description"
     ></iframe>
     <div class="video-card-label">
       <strong>Testimony — Location</strong>
       <span>Interviewee name · Date</span>
     </div>
   </div>
   ```
6. Save, commit, push

---

## Optional: Using Git LFS for large image files

If the image files make the repo too large (GitHub's soft limit is ~1 GB):

```bash
# Install Git LFS
git lfs install

# Track image formats
git lfs track "*.jpg" "*.JPG" "*.png" "*.MP4"

# Add .gitattributes
git add .gitattributes
git commit -m "Add Git LFS tracking for media files"

git push origin main
```

---

## Troubleshooting

| Problem | Solution |
|---|---|
| `git push` asks for password | Use a Personal Access Token, not your GitHub password |
| Images not showing on live site | Check that paths in HTML match exactly (case-sensitive on GitHub Pages) |
| Site not updating after push | Wait 2–3 minutes; GitHub Pages takes time to rebuild |
| Large files rejected | Use Git LFS (see above) or host images on Google Drive / Cloudinary |
| Merge conflict | Run `git pull origin main` first, then re-push |

---

## Contact for technical help

If you run into issues, the full website source is maintained at:  
https://github.com/Ngue-Um/ecomusee-malume

For questions about the website build, refer back to this guide or contact the project team.
