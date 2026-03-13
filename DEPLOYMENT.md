# Deployment Guide

## Quick Deploy to GitHub Pages

### 1. Push to GitHub

```bash
# Initialize git (if not already)
git init
git add .
git commit -m "Initial commit: AI Concepts Playground"
git remote add origin https://github.com/YOUR_USERNAME/ai-playground.git
git branch -M main
git push -u origin main
```

### 2. Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages**
2. Set **Source** to `Deploy from a branch`
3. Select `main` branch and `/dist` folder
4. Save

### 3. Update `vite.config.js` (optional)

If deploying to `https://github.com/YOUR_USERNAME/ai-playground`:

```javascript
export default defineConfig({
  plugins: [react()],
  base: '/ai-playground/',  // <- Add this
  build: {
    outDir: 'dist',
  }
})
```

Then rebuild and push:

```bash
npm run build
git add dist/
git commit -m "Build: static site"
git push
```

Your site will be live at: `https://YOUR_USERNAME.github.io/ai-playground`

---

## Deploy to Netlify

### Option A: Via Git Push

1. Go to [Netlify](https://netlify.com) and sign up
2. Click **Add new site** → **Import an existing project**
3. Connect your GitHub account and select `ai-playground` repo
4. Build command: `npm run build`
5. Publish directory: `dist`
6. Deploy

Netlify will auto-build on every git push.

### Option B: Via Drag & Drop

```bash
npm run build
```

Then drag the `dist/` folder to [Netlify Drop](https://app.netlify.com/drop).

Your site gets a free `.netlify.app` URL instantly.

---

## Deploy to Vercel

1. Go to [Vercel](https://vercel.com) and sign up
2. Import your GitHub repository
3. Framework: **Vite**
4. Build command: `npm run build`
5. Output directory: `dist`
6. Deploy

Vercel auto-deploys on git push. Free tier includes unlimited deployments.

---

## Deploy to Firebase Hosting

```bash
# Install Firebase CLI
npm install -g firebase-tools

# Login
firebase login

# Initialize
firebase init hosting

# When prompted:
# - Hosting directory: dist
# - Single page app: yes

# Build & deploy
npm run build
firebase deploy
```

---

## Environment Variables (if needed)

All configuration is in localStorage — no `.env` file needed. The user's API key is never exposed.

If you ever need to add environment variables, add to `vite.config.js`:

```javascript
export default defineConfig({
  define: {
    __VITE_API_URL__: JSON.stringify(process.env.VITE_API_URL || 'https://api.anthropic.com')
  }
})
```

---

## Monitoring & Analytics

Both Netlify and Vercel include free analytics dashboards.

For custom tracking (e.g., lab usage), add a simple script to `index.html`:

```html
<script async src="https://cdn.youranalytics.com/script.js"></script>
```

---

## Custom Domain

All platforms support custom domains. Usually:

1. Add your domain in hosting settings
2. Update DNS records (A/CNAME) to point to the platform
3. Enable free HTTPS (auto)

---

## Questions?

- **Netlify**: https://docs.netlify.com/
- **Vercel**: https://vercel.com/docs
- **GitHub Pages**: https://docs.github.com/en/pages
- **Firebase**: https://firebase.google.com/docs/hosting
