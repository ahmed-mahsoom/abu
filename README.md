# ⚙️ Abu Talal Trading EST — Official Website

A high-performance, responsive website for **Abu Talal Trading EST**, an auto and forklift spare parts supplier in **Sinayiat Al Thuqba, Al Khobar, Saudi Arabia**.

---

## ⚡ Vercel Deployment Guide

This project is 100% configured and optimized for **Vercel** deployment with edge caching, byte-range video streaming support, and security headers.

### Option 1: Deploy via GitHub (Recommended)

1. Create a new repository on your GitHub / GitLab / Bitbucket account (e.g. `abu-talal-trading`).
2. In your terminal, link your remote repository and push:
   ```powershell
   git remote add origin https://github.com/YOUR_USERNAME/abu-talal-trading.git
   git push -u origin main
   ```
3. Go to **[vercel.com/new](https://vercel.com/new)**.
4. Import the repository and click **Deploy**.
5. Vercel will automatically read `vercel.json` and deploy the site to a live URL (e.g. `https://abu-talal-trading.vercel.app`) with free global SSL, CDN caching, and automated preview deployments on git push.

---

### Option 2: Deploy via Vercel CLI

1. If you have Node.js / npm installed:
   ```powershell
   npm i -g vercel
   ```
2. In this folder (`c:\Users\SAMSUNG\newproject`), run:
   ```powershell
   vercel
   ```
3. For immediate production deployment:
   ```powershell
   vercel --prod
   ```

---

### Option 3: Deploy via Vercel Dashboard (Drag & Drop)

1. Go to **[vercel.com](https://vercel.com)**.
2. Under "Add New...", select **Project** and drag and drop this project directory.
3. Click **Deploy**.

---

## 🛠️ Vercel Optimizations (`vercel.json`)

- **Edge CDN Media Caching:** `assets/*` (including the 5.4 MB 1080p `engine-hero.mp4` video, poster still, and category sprite sheets) are served with `Cache-Control: public, max-age=31536000, immutable` and `Accept-Ranges: bytes` for instantaneous seeking and scrubbing without bandwidth lag.
- **Clean URLs:** Auto-configured with `"cleanUrls": true` and `"trailingSlash": false`.
- **Security Headers:** Includes `X-Content-Type-Options: nosniff`, `X-Frame-Options: SAMEORIGIN`, and `Referrer-Policy: strict-origin-when-cross-origin`.

---

## 🏗️ Page Architecture & Sequence

The website is structured into two main sequential experiences:

### 1. Full-Screen Engine-Video Intro (Top of Page)
- **Visual Staging:** A full-screen (`100vh` sticky stage inside a `230vh` scroll track) interactive 3D engine video breakdown.
- **Hardware-Accelerated Canvas Rendering Cache:**
  - High-performance `<canvas id="introCanvas">` using `desynchronized: true` and `alpha: false` rendering context.
  - Automatically pre-caches frames as GPU `ImageBitmap` buffers into an in-memory `Map` (90 frames on desktop, 60 frames on mobile).
  - Eliminates browser video decoder seek lag (`currentTime` bottleneck), enabling instantaneous 60fps/120fps scrubbing backwards and forwards.
- **Background Auto-Render Engine:**
  - Automatically spins up upon page load in the background, streaming the video at accelerated rate (`playbackRate = 2.5`) with `requestVideoFrameCallback` to pre-render and cache all keyframes in ~1.5 seconds.
  - Once rendering completes, the background video decoder is cleanly paused to preserve system battery and CPU/GPU resources.
  - Real-time scrub status pill badge shows live auto-render progress (`⚡ Auto-rendering cache... (X%)` → `⚡ 60fps Cache Ready`).
- **Scroll-Controlled Playback & Lerp Smoothing:**
  - As visitors scroll down through this intro section, the video advances in sync with scroll progress; scrolling back up smoothly rewinds it with 0.2 lerp smoothing.
  - Cache-fault tolerance: if the user scrolls before pre-rendering finishes, it instantly falls back to the nearest cached frame or decodes on-demand without stutter or black frames.
- **Intro UI & Controls:**
  - Branding header with logo and `Skip Intro to Catalogue ↓` button.
  - Centered typography: `Engineered for Reliability` with golden yellow accents.
  - Interactive scrub pill: `⚙️ Scrubbing Engine (X%) · ⚡ 60fps Cache` with live progress bar.
  - Prominent prompt linking directly into the homepage content.
- **Fallbacks & Accessibility:**
  - High-resolution poster frame [assets/engine-poster.jpg](file:///c:/Users/SAMSUNG/newproject/assets/engine-poster.jpg) extracted at 1920×1080 primed instantly before caching starts.
  - Reduced-motion support (`@media (prefers-reduced-motion: reduce)`) halts auto-render and displays the static poster without video scrubbing.
  - Responsive crop (`object-fit: cover; object-position: center center`) for mobile devices.

---

### 2. Original Homepage Content (In Existing Order & Unrewritten)
Directly following the video intro, the complete original homepage unfolds in its exact content sequence:

1. **Topline Info Bar:**
   - Location: `📍 Sinayiat Al Thuqba · Al Khobar, Saudi Arabia`
   - Direct contacts: `📞 +966 56 363 0419` & `✉️ abutalaltradingest@gmail.com`
2. **Sticky Header & Navbar:**
   - Brand mark [assets/logo.png](file:///c:/Users/SAMSUNG/newproject/assets/logo.png)
   - Navigation links: *Spare Parts*, *Why Choose Us*, *How to Order*, *Part Enquiry*, *Location & Contact*
   - Direct action buttons: *Find a Part* and *WhatsApp*
   - Responsive mobile drawer menu
3. **Original Homepage Hero Section:**
   - Grayscale parts collage [assets/catalogue-parts-collage.png](file:///c:/Users/SAMSUNG/newproject/assets/catalogue-parts-collage.png) on right side with charcoal gradient overlay
   - Tagline: `⚙️ Genuine OEM & Quality Aftermarket Parts`
   - Headline: `Dependable Auto & Forklift Spare Parts in Al Khobar`
   - Introduction: Serving individual car owners, mechanics, repair workshops, and fleet operators
   - Action buttons: `🔍 Find a Part`, `📞 Call Us Directly`, `💬 WhatsApp Chat`
   - Live pulse indicator dot and fitment guarantee badge
4. **Original Quick Stats Bar:**
   - *Sinayiat Al Thuqba*, *Comprehensive Coverage*, *Trusted Quality*
5. **Original Part Enquiry Section & Form (`#part-enquiry`):**
   - Pre-check availability guidance
   - Fast direct contact options (WhatsApp, Call, Email)
   - Form fields: Make, Model, Year, Category dropdown, Part Name or Part Number, Name, Phone/WhatsApp, Additional Details / Fitment Notes
   - Dual submission handlers: **💬 Send via WhatsApp ↗** and **✉️ Send via Email ↗**
6. **Original Parts Catalogue Section (`#parts-catalog`):**
   - All 16 product categories with component descriptions
   - Filter tabs: *All 16 Categories*, *Engine & Powertrain*, *Suspension & Brakes*, *Forklift & Industrial*, *Electrical & Climate*, *Filters & Maintenance*
   - Instant real-time search input
   - Grayscale sprite sheet category images [assets/category-image-sheet.png](file:///c:/Users/SAMSUNG/newproject/assets/category-image-sheet.png)
   - Click-to-enquire functionality
7. **Original Why Choose Us Section (`#why-choose-us`):**
   - 4 value propositions: Expert Parts Identification, Broad Product Selection, Competitive Pricing, Dedicated Customer Service
   - Target Customer Segments Strip (Car Owners, Mechanics, Workshops, Fleet Operators)
8. **Original How to Get the Right Part Section (`#how-to-order`):**
   - 3-step guide with VIN / Istimara and photo tips
9. **Original Location & Contact Details Section (`#contact-location`):**
   - Physical address in Sinayiat Al Thuqba, Al Khobar
   - Phone, WhatsApp, Email, Instagram handle (`@abu.talal.trading.est`)
   - Working hours placeholder
   - Direct Google Maps link
10. **Original Footer:**
    - Full copyright, disclaimers, and business details

---

## 📦 Project Assets (Deployment Ready)

All media assets are stored inside the project's [assets/](file:///c:/Users/SAMSUNG/newproject/assets/) directory and referenced with relative URLs:
- `assets/engine-hero.mp4` (5.4 MB 1080p Engine Video)
- `assets/engine-poster.jpg` (321 KB 1080p Poster Still)
- `assets/catalogue-parts-collage.png` (Grayscale Parts Collage for Original Hero)
- `assets/category-image-sheet.png` (CSS Sprite Sheet for 16 Categories)
- `assets/logo.png` (Official Abu Talal Trading EST Logo)
- `favicon.ico`

---

## 🚀 Running the Website Locally

```powershell
python serve.py
```
Open **[http://localhost:8000/](http://localhost:8000/)** in your browser.
