# AeroBMSCE Website Revamp — Technical Recruitment Task

Revamped, institutional, desktop-optimized web application for **AeroBMSCE** (the collegiate aeromodelling and unmanned aerial vehicle lab of B.M.S. College of Engineering).

---

## 1. Flaws of the Original Website
* **Fragmented Information Architecture:** Critical club details, achievements, and technical fleet data were scattered across disparate legacy files (`index.html`, `journey.html`, `partners.html`) with no unified narrative flow or structured navigation[cite: 1].
* **Broken Navigation & Non-functional Anchors:** Internal hyperlinks across the top bar were either dead (`href="#"`), misdirected, or pointed to nonexistent anchors, preventing visitors from discovering club information[cite: 1].
* **Severe Asset Scaling & Distortion:** The original markup lacked modern responsive wrappers and aspect-ratio constraints, resulting in aircraft and team photos from the `images/` directory being stretched, pixelated, or misaligned across desktop viewports[cite: 1, 2].
* **Inconsistent Visual Hierarchy & Design Language:** The original styling lacked a unified design system; typography, buttons, margin spacing, and contrast ratios varied across pages without visual cohesion.

---

## 2. Design Route & UI/UX Decisions
* **Institutional Aerospace Aesthetic:** Replaced generic AI template dark grids with an authentic collegiate engineering identity: clean architectural slate (`#f8fafc`), deep aerospace navy (`#0f172a`), royal blue accents (`#1d4ed8`), and crisp white telemetry cards[cite: 2].
* **Dual-Module Scrollytelling Architecture:** 
  * **"Who We Are":** Implemented a pinned scroll-storytelling track cycling through all four engineering wings (Team Yaksha, Team Blue Impulse, Team Flying Phantoms, Team Vectors)[cite: 1]. The data card remains pinned on the left while full, unobstructed workshop and flight-line photos cross-fade on the right[cite: 1].
  * **"What We Build":** Applied the same pinned scrollytelling mechanism to showcase the aircraft fleet (SAE Micro-Class, Multi-Mission VTOL, Fin Testbed) alongside structural dimensions, propulsion specs, and payload ratios[cite: 1].
* **Balanced Wheel Transition Math:** Engineered proportional scroll thresholds using normalized progress ratios (`Math.min(maxIdx, Math.floor(prog * count))`) so every slide triggers on an identical, snappy 1–2 wheel clicks without lag or hanging on the initial slide[cite: 2].
* **Interactive Mission Debrief Modals:** Built client-side modal windows for major milestones—including the SAE Aero Design West (Fort Worth, Texas) 2nd Place MATLAB Simulation Award and the SAE Aerothon 1st Place Unique Technology Award—allowing reviewers to inspect deep technical logs without cluttering the main layout[cite: 1].
* **Dynamic Partnership Autofill:** Linked the sponsorship tiers (Platinum, Gold, Silver, Technical) directly to the partnership transmission form, auto-populating tier details on click for seamless UX[cite: 1].

---

## 3. Problem / Edge Case Faced & Resolution
* **Problem:** Uneven scroll dwell time and image obstruction in the initial scrollytelling layout.
* **How it occurred:** The first slide in the pinned container was capturing both the entry scroll offset and its proportional segment, causing slide 1 to require almost double the scroll effort of subsequent slides. Furthermore, standard text overlays were overlapping the center of team photographs, obscuring member faces and aircraft details.
* **Resolution:** 
  1. Restructured the layout into an asymmetric 5:7 split grid where all textual telemetry is self-contained in a structured card on the left, leaving the right 60% entirely clear for unobstructed, high-resolution imagery.
  2. Shortened the scroll track container heights from `400vh` to a lightweight `140vh`/`120vh` and rewrote the progress calculation to sample active windows evenly, ensuring uniform and responsive transition timing across all subteams and aircraft.
  3. Enforced explicit relative asset paths (`./images/filename.jpg`) across all image sources to prevent 404 path resolution failures when deployed to GitHub Pages repository subpaths[cite: 1, 2].
