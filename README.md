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

## CSP (Content Security Policy)

If your site has a strict CSP, add these to allow Clarity:

```
script-src https://www.clarity.ms
connect-src https://www.clarity.ms https://clarity.ms
```

## Resources

- [Clarity Setup Docs](https://learn.microsoft.com/en-us/clarity/setup-and-installation/clarity-setup)
- [Clarity Demo](https://clarity.microsoft.com/demo/projects/view/3t0wlogvdz/heatmaps)
