# eplus Live Stream Player

A static HTML video player using [Artplayer.js](https://artplayer.org/) with HLS support, designed for watching eplus.jp live streams. Deployable to GitHub Pages with zero build steps.

## 📁 Project Structure

```
eplus_player/
├── index.html          # Main player page
├── README.md           # This file
├── assets/
│   ├── loading.gif     # Loading spinner animation
│   ├── state.svg       # Play state icon
│   └── indicator.svg   # Live indicator icon
└── lib/
    ├── artplayer.js    # Artplayer.js v5 (video player)
    └── hls.min.js      # hls.js v1 (HLS stream support)
```

## 🚀 Deploy to GitHub Pages

### Option 1: Quick Deploy

1. **Create a new GitHub repository** (e.g., `eplus-player`)

2. **Push this folder to the repo:**
   ```bash
   cd eplus_player
   git init
   git add .
   git commit -m "Initial commit: eplus live stream player"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/eplus-player.git
   git push -u origin main
   ```

3. **Enable GitHub Pages:**
   - Go to your repo → **Settings** → **Pages**
   - Under "Source", select **Deploy from a branch**
   - Choose **main** branch, **/ (root)** folder
   - Click **Save**

4. **Access your player** at:
   ```
   https://YOUR_USERNAME.github.io/eplus-player/
   ```

### Option 2: Use GitHub Actions (automatic)

GitHub Pages will automatically serve static files from the `main` branch. No build action needed.

## 🔧 Usage

### Updating Stream URL

The CloudFront signed URL **expires after ~1 hour**. To refresh:

1. Visit the eplus player page in your browser
2. Open DevTools (`F12`) → **Network** tab
3. Filter for `m3u8` requests
4. Copy the new `Policy`, `Signature`, and `Key-Pair-Id` values
5. Paste them into the input fields on the player page
6. Click **▶ Apply & Reload Player**

### Editing URL in Code

You can also edit the default URL values directly in `index.html`. Look for the `<input>` and `<textarea>` elements with IDs:
- `baseUrl` — the base HLS manifest URL
- `paramPolicy` — CloudFront Policy parameter
- `paramSignature` — CloudFront Signature parameter  
- `paramKeyPairId` — CloudFront Key-Pair-Id parameter

## 🎬 Player Features

- **Live mode** with live indicator
- **HLS streaming** via hls.js
- **Quality selector** (SD 480P / HD 720P)
- **Picture-in-Picture** (PiP)
- **Screenshot capture**
- **Fullscreen** and web fullscreen
- **Flip** and aspect ratio controls
- **Playback rate** control
- **Auto-play** (muted, to comply with browser policies)
- **Airplay** support
- **Lock controls** (mobile)
- **Auto orientation** (mobile)

## ⚠️ Notes

- The stream URL contains CloudFront authentication tokens that expire after ~1 hour
- The player auto-plays muted to comply with browser autoplay policies — unmute manually
- CORS may affect some features; the HLS.js library handles most cross-origin scenarios
- This is a **static site** with no server-side components — all processing happens in the browser

## 📄 License

This project is for personal use. Artplayer.js is licensed under MIT. hls.js is licensed under Apache 2.0.
