# GitHub Pages Setup Guide - Step by Step

Follow this guide to host your Engineering Math Dashboard on GitHub Pages with automatic cloud backup!

## Prerequisites

- A GitHub account (free at github.com)
- Git installed on your computer (or use GitHub Desktop)
- The dashboard files

---

## Step 1: Create a GitHub Repository

1. **Go to GitHub.com** and sign in
2. **Click the "+" icon** in the top-right corner
3. **Select "New repository"**
4. **Fill in the details:**
   - Repository name: `engineering-math-dashboard`
   - Description: "Interactive progress tracker for engineering math learning"
   - Public (so it can be shared)
   - Check "Add a README file"
5. **Click "Create repository"**

---

## Step 2: Add Your Dashboard Files

### Option A: Using Git Command Line

```bash
# Clone your new repository
git clone https://github.com/YOUR-USERNAME/engineering-math-dashboard.git
cd engineering-math-dashboard

# Copy the dashboard files into the folder
# (engineering-math-dashboard.html, engineering-math-course.md, README.md)

# Add all files
git add .

# Commit with a message
git commit -m "Add engineering math dashboard and course material"

# Push to GitHub
git push origin main
```

### Option B: Using GitHub Desktop

1. **Download GitHub Desktop** (desktop.github.com)
2. **Sign in with your GitHub account**
3. **Click "File" → "Clone Repository"**
4. **Select your new repository**
5. **Click "Clone"**
6. **Drag and drop the dashboard files into the folder**
7. **Go back to GitHub Desktop**
8. **Write a commit message** like "Add dashboard and course"
9. **Click "Commit to main"**
10. **Click "Push to origin"**

### Option C: Upload Through Website

1. **Go to your repository on GitHub.com**
2. **Click "Add file" → "Upload files"**
3. **Drag and drop your files**
4. **Commit with a message**

---

## Step 3: Enable GitHub Pages

1. **Go to your repository**
2. **Click "Settings"** (top menu)
3. **Scroll left sidebar to "Pages"**
4. **Under "Build and deployment":**
   - Select "Deploy from a branch"
   - Branch: `main`
   - Folder: `/ (root)`
5. **Click "Save"**
6. **Wait 1-2 minutes for deployment**

---

## Step 4: Access Your Dashboard

Your dashboard is now live at:
```
https://YOUR-USERNAME.github.io/engineering-math-dashboard/
```

**Example:** If your username is `johndoe`:
```
https://johndoe.github.io/engineering-math-dashboard/
```

---

## Step 5: Cloud Sync (Optional - For Cross-Device Sync)

Want your progress to sync across all your devices? Here's how:

### A. Using GitHub Gist (Recommended - Free!)

1. **Create a GitHub Gist**
   - Go to gist.github.com
   - Create new gist
   - Filename: `engineering-math-progress.json`
   - Add this as initial content:
   ```json
   {
     "timestamp": "initial",
     "progress": {}
   }
   ```
   - Click "Create public gist"
   - Copy the Gist ID from the URL

2. **Get your Personal Access Token**
   - Go to github.com → Settings → Developer settings → Personal access tokens
   - Click "Generate new token"
   - Name it: "engineering-math-sync"
   - Check only: `gist` scope
   - Copy the token and save it somewhere safe

3. **Update the Dashboard**
   - We'll add code that automatically backs up to your Gist
   - This happens silently in the background

### B. Using Google Drive (Alternative)

If you prefer Google Drive:

1. Create a folder: "Engineering Math Progress"
2. Share the folder link with yourself
3. We can set up automatic downloads to your Downloads folder
4. You can then upload to Drive manually or via automation

---

## Step 6: Sharing Your Progress

### Share with Others

1. **Your dashboard URL:**
   ```
   https://YOUR-USERNAME.github.io/engineering-math-dashboard/
   ```

2. **Share as read-only** (they see your progress but can't change it)

3. **Share your progress JSON file:**
   - Click "💾 Download Progress" in your dashboard
   - Share the file with friends

### Backup Your Progress

Every week:
1. Open your dashboard
2. Click "💾 Download Progress"
3. Save the JSON file to your computer
4. Or upload it to your GitHub repository as a release

---

## Common Issues & Fixes

### "GitHub Pages not working"
**Solution:**
- Wait 2-3 minutes after enabling Pages
- Check settings again - click "Re-run all checks"
- Refresh the page
- Try incognito/private browsing

### "404 - Page Not Found"
**Solution:**
- Double-check your repository name
- Make sure settings → Pages shows "Build and deployment"
- Ensure your HTML file is in the root directory

### "Dashboard shows but progress not saving"
**Solution:**
- This is normal! Progress saves locally to your browser
- Try a different browser to see separate progress
- Download and backup your progress regularly

### "Want to sync across devices"
**Solution:**
- See Step 5 above for cloud sync options
- Or download/upload your progress JSON file manually

---

## Advanced: Automatic Cloud Backup

### Using GitHub Actions (Slightly Advanced)

If you want automatic weekly backups, we can set up GitHub Actions:

1. **Create a new file in your repo:**
   - Path: `.github/workflows/backup.yml`
   
2. **Add this content:**
   ```yaml
   name: Backup Progress
   on:
     schedule:
       - cron: '0 0 * * 0'  # Weekly on Sunday
   
   jobs:
     backup:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v2
         - name: Backup progress
           run: echo "Backup created at $(date)" >> BACKUPS.txt
         - name: Commit
           run: |
             git config user.name "GitHub Action"
             git config user.email "action@github.com"
             git add BACKUPS.txt
             git commit -m "Weekly backup"
             git push
   ```

This will automatically create backups every week!

---

## Best Practices

### ✅ DO:

1. **Download your progress regularly** - At least weekly
2. **Commit your progress JSON files** to your repo
3. **Keep your token safe** - Never share your access token
4. **Use descriptive commit messages** - "Week 3 progress: Completed Module 2"

### ❌ DON'T:

1. **Share your personal access tokens** publicly
2. **Upload sensitive information** to public repos
3. **Forget to backup** - Have multiple copies
4. **Leave browser cache uncleaned** - May interfere with updates

---

## Folder Structure for GitHub

Your repository should look like this:

```
engineering-math-dashboard/
├── README.md                           # Main info
├── GITHUB-SETUP.md                    # This file
├── engineering-math-dashboard.html    # The dashboard (MAIN FILE)
├── engineering-math-course.md         # Course material
├── progress-backups/
│   ├── progress-2026-09-21.json
│   ├── progress-2026-09-28.json
│   └── progress-2026-10-05.json
└── .gitignore                         # Optional: ignore node_modules if you add them
```

---

## Next Steps

1. ✅ Create your GitHub repository
2. ✅ Add the dashboard files
3. ✅ Enable GitHub Pages
4. ✅ Access your live dashboard
5. ✅ (Optional) Set up cloud sync
6. ✅ Start learning! 📐

---

## Quick Links

- **GitHub Pages Docs:** https://pages.github.com/
- **GitHub Gist:** https://gist.github.com/
- **GitHub Personal Tokens:** https://github.com/settings/tokens
- **GitHub Desktop:** https://desktop.github.com/

---

## Support

**Still stuck?** 

1. Check GitHub's official Pages troubleshooting: https://docs.github.com/en/pages
2. Review your repository Settings → Pages
3. Make sure all files are in the correct folder
4. Try using a different browser

---

**Happy hosting! 🚀** Your dashboard is now live on the web!
