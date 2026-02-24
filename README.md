# Microsoft Clarity Test Setup

A simple test page to try out [Microsoft Clarity](https://clarity.microsoft.com/) for heatmaps, session recordings, and user behavior analytics.

## Quick Start

### 1. Get your Clarity Project ID

1. Go to [clarity.microsoft.com](https://clarity.microsoft.com/) and sign in
2. Create a new project or select an existing one
3. Go to **Settings** → **Setup** → **Get tracking code**
4. Copy your project ID (the alphanumeric string in the script)

### 2. Add your Project ID

Open `index.html` and replace `YOUR_PROJECT_ID` with your actual project ID:

```html
})(window, document, "clarity", "script", "YOUR_PROJECT_ID");
```

### 3. Run the page

**Option A: Open directly**
```bash
open index.html
```

**Option B: Use a local server** (recommended for full functionality)
```bash
npx serve .
# or
python3 -m http.server 8000
```
Then visit `http://localhost:8000` (or the port shown).

### 4. Verify installation

- **Clarity dashboard:** Check your project for real-time data and "Watch now" for live recordings
- **Browser DevTools:** Network tab → filter for `collect` → you should see POST requests to `https://www.clarity.ms/collect` when you interact with the page

## What to test

- **Clicks:** Use the buttons to generate click heatmap data
- **Forms:** Fill out and submit the form
- **Scroll:** Scroll down the page to see scroll depth heatmaps
- **Session recordings:** Your full session will be recorded for playback

## Deploy to Contentstack Launch

To test Clarity on a live URL via Contentstack Launch:

### Option A: File upload

1. **Create a zip** of the project (include `index.html` at the root):
   ```bash
   zip -r test-clarity.zip index.html README.md
   ```

2. **In Contentstack Launch:**
   - Log in at [Contentstack](https://www.contentstack.com/login/) → **Launch**
   - Click **+ New Project** → **Upload a file**
   - Drag and drop the zip or browse to upload
   - Click **Next**

3. **Build and Output Settings** (static site):
   - **Framework Preset:** Select **Other**
   - **Output Directory:** `.` (or leave as root)
   - **Build Command:** Leave **blank** (Launch skips build for static sites)

4. Click **Deploy**

5. Once deployed, visit the Launch URL (e.g. `https://your-project.launch.contentstack.com`) and interact with the page. Clarity will start collecting data.

### Option B: GitHub

1. Push this project to a GitHub repo
2. In Launch → **+ New Project** → **Import from GitHub**
3. Select the repo and branch
4. Use the same Build settings as above (Framework: Other, Build Command: blank)
5. Click **Deploy**

### Verify on Launch

After deployment, open your Launch URL, interact with the page, then check [clarity.microsoft.com](https://clarity.microsoft.com/) for recordings and heatmaps. Data may take a few minutes to appear.

---

## CSP (Content Security Policy)

If your site has a strict CSP, add these to allow Clarity:

```
script-src https://www.clarity.ms
connect-src https://www.clarity.ms https://clarity.ms
```

## Resources

- [Clarity Setup Docs](https://learn.microsoft.com/en-us/clarity/setup-and-installation/clarity-setup)
- [Clarity Demo](https://clarity.microsoft.com/demo/projects/view/3t0wlogvdz/heatmaps)
- [Contentstack Launch](https://www.contentstack.com/docs/developers/launch) — [Host a Static Site](https://www.contentstack.com/docs/developers/launch/host-a-static-site)
