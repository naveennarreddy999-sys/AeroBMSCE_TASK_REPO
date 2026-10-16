# AeroBMSCE Website Revamp — Technical Recruitment Task
---

## 1. Flaws of the Original Website
* **Broken Navigation & Dead End Links:** The original top navigation contained non-functional hyperlinks (`href="#"`), mispointed anchor targets, and stray layout elements that prevented smooth user discovery across pages.
* **Dislocated Information Architecture:** Club achievements, subteams, and ongoing technical fleet research were fragmented across detached legacy files (`index.html`, `journey.html`, `partners.html`).
* **Severe Asset Scaling & Distortion:** The original markup lacked modern responsive wrappers and aspect-ratio constraints, resulting in aircraft and team photos from the `images/` directory being stretched, pixelated, or misaligned across desktop viewports.
* **Visual Incoherence & Contrast Failures:** Lacked a unified design system; arbitrary fonts, unconstrained container margins, and unstyled form fields degraded the institutional credibility of an internationally competitive aerospace club.

---

## 2. Design Route & UI/UX Decisions
* **Institutional Aerospace Identity:** Implemented an official collegiate engineering design system: clean architectural slate (`#f8fafc`), deep aerospace navy (`#0f172a`), royal blue accents (`#1d4ed8`), and clean monospaced telemetry data tables.
* **Interactive Wipe Slider (Airframe Inspector):** Engineered an interactive horizontal wipe slider allowing evaluators to compare the CAD structural topology with the real manufactured balsa-carbon airframe in real-time.
* **Scroll-Linked Avionics HUD:** Built a fixed telemetry widget that maps page scroll progress directly to an **Altitude Gauge** (`0 FT` to `10,000 FT`) and **Airspeed Indicator**, giving evaluators a responsive flight simulation experience.
* **Live Mission Horizon Countdown:** Incorporated a real-time countdown calculating days, hours, and minutes remaining until the upcoming NACDEC 2026 / NITK Drone Racing campaigns.
* **Fullscreen Hangar Lightbox Modal:** Built an interactive gallery lightbox supporting keyboard arrow navigation (`←`, `→`, and `Esc` to close) for high-resolution inspection of workshop photos.
* **Desktop 3D Tilt Physics:** Applied dynamic mouse-tracking tilt physics across fleet and sponsorship cards for enhanced depth without degrading browser performance.

---

## 3. Problem / Edge Case Faced & Resolution
* **Problem:** Ensuring complex interactive avionics widgets (scroll-linked altitude meter, progress bar, parallax background, and 3D tilt calculations) run smoothly at 60 FPS without layout thrashing or interfering with keyboard navigation.
* **How it occurred:** Running unthrottled JavaScript listeners on `window.onscroll` and `window.onmousemove` can trigger heavy DOM recalculations and frame drops on budget laptops or trackpads.
* **Resolution:** 
  1. Configured all scroll listeners with `{ passive: true }` to separate scroll execution from main-thread rendering.
  2. Isolated animated properties to GPU-accelerated transforms (`transform`, `opacity`, and `width`) and added `@media (prefers-reduced-motion: reduce)` rules to ensure full accessibility compliance.
  3. Enforced explicit relative paths (`./images/filename.jpg`) across all image sources to prevent 404 path resolution failures when deployed to GitHub Pages repository subpaths.
