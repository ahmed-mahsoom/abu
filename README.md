# ⚙️ Abu Talal Trading EST — Official Website

A high-performance, responsive website for **Abu Talal Trading EST**, an auto and forklift spare parts supplier in **Sinayiat Al Thuqba, Al Khobar, Saudi Arabia**.

---

## 🏗️ Page Architecture & Sequence

The website is structured into two main sequential experiences:

### 1. Full-Screen Engine-Video Intro (Top of Page)
- **Visual Staging:** A full-screen (`100vh` sticky stage inside a `230vh` scroll track) interactive 3D engine video breakdown (`assets/engine-hero.mp4`).
- **Scroll-Controlled Playback:** As visitors scroll down through this intro section, the video plays forward in sync with scroll progress; scrolling back up smoothly rewinds it.
- **Fluid Lerp Interpolation:** Uses linear interpolation via `requestAnimationFrame` to ensure seamless, stutter-free frame seeking.
- **Intro UI & Controls:**
  - Branding header with logo and `Skip Intro to Catalogue ↓` button.
  - Centered typography: `Engineered for Reliability` with golden yellow accents.
  - Interactive scrub pill: `⚙️ Scroll to scrub engine (X%)` with live progress bar.
  - Prominent prompt linking directly into the homepage content.
- **Fallbacks & Accessibility:**
  - High-resolution poster frame [assets/engine-poster.jpg](file:///c:/Users/SAMSUNG/newproject/assets/engine-poster.jpg) extracted at 1920×1080.
  - Reduced-motion support (`@media (prefers-reduced-motion: reduce)`) displays the static poster without scroll-jacked video scrubbing.
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
