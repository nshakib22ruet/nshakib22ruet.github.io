# Md. Najmus Shakib — Portfolio Website

This repo contains a single-page portfolio site (`index.html`). Everything — content, styling, and behavior — lives in that one file, so all edits below are made by opening `index.html` in any text editor (VS Code, Notepad++, GitHub's web editor, etc.), changing the relevant part, saving, and pushing to GitHub.

No build tools, no npm install — just edit and push.

---

## 📁 Files in this repo

| File | Purpose |
|---|---|
| `index.html` | The entire website (structure + styling + logic) |
| `profile.jpg` | Your profile photo shown in the hero section |
| `MdNajmusShakib_CV.pdf` | The CV file people download from the CV page |

---

## 1. Adding a new Skill category (a new "datasheet" card)

Skill categories are the clickable cards under **Technical Skills** (e.g. "Programming Languages", "Embedded Systems & IoT").

**Find this in `index.html`:** search for `const skillsData = [`

You'll see a list like this:

```js
const skillsData = [
  { id: "U1", icon: "fa-solid fa-code", title: "Programming Languages",
    blurb: "Core languages used across firmware development, control-system modeling, and data analysis.",
    items: ["C", "C++", "Python", "MATLAB"] },
  { id: "U2", icon: "fa-solid fa-microchip", title: "Embedded Systems & IoT",
    blurb: "Firmware and connectivity skills behind ESP32-based sensor systems and wireless dashboards.",
    items: ["ESP32", "Arduino", "Bluetooth Low Energy (BLE)", "Sensor Interfacing", "Embedded C"] },
  ...
];
```

**To add a new category**, copy one block and paste it before the closing `];`, then edit the fields:

```js
  { id: "U7", icon: "fa-solid fa-robot", title: "Robotics",
    blurb: "Short one-line description of what this category covers.",
    items: ["Item One", "Item Two", "Item Three"] }
```

- `id` — just a label, keep it unique (U7, U8, U9...)
- `icon` — a [Font Awesome](https://fontawesome.com/search?o=r&m=free) icon class (e.g. `fa-solid fa-robot`)
- `title` — the card's heading
- `blurb` — one-line description shown inside the pop-up
- `items` — array of skill names in that category

⚠️ **Don't forget the comma** after the previous block's closing `}` when adding a new one.

---

## 2. Adding a new topic/item inside an existing skill (e.g. adding to "Machine Learning & Data Analysis")

Find the category you want in `skillsData` (e.g. `title: "Machine Learning & Data Analysis"`) and just add a new item to its `items` array:

```js
  { id: "U3", icon: "fa-solid fa-chart-line", title: "Machine Learning & Data Analysis",
    blurb: "Applied modeling techniques used for prediction and analysis in sensor-driven projects.",
    items: ["Machine Learning Fundamentals", "Quadratic Regression", "Data Analysis", "NumPy", "Pandas", "Matplotlib", "TensorFlow Lite Micro"] },
```
(new item `"TensorFlow Lite Micro"` added at the end)

That's it — no other changes needed.

---

## 3. Adding a new Project

Projects appear as name-only horizontal slides under **Projects & Tasks**. Clicking one opens the full project page.

**Find this in `index.html`:** search for `const projectsData = [`

```js
const projectsData = [
  { id: "P1", badge: "IoT / Machine Learning",
    title: "ESP32 IoT Weather & Flood Monitoring System",
    description: "An intelligent environmental tracking system utilizing ESP32 with Bluetooth Low Energy (BLE), an SH1106 OLED interface, and an embedded quadratic regression model for real-time flood risk prediction.",
    tags: ["ESP32", "BLE", "Regression Model", "Embedded C"],
    github: "https://github.com/nshakib22ruet/Project-1-ESP32-Weather-Flood-Monitoring-System" }
];
```

**To add a new project**, add a new object after the last one (remember the comma!):

```js
const projectsData = [
  { id: "P1", badge: "IoT / Machine Learning",
    title: "ESP32 IoT Weather & Flood Monitoring System",
    description: "...",
    tags: ["ESP32", "BLE", "Regression Model", "Embedded C"],
    github: "https://github.com/nshakib22ruet/Project-1-ESP32-Weather-Flood-Monitoring-System" },
  { id: "P2", badge: "IoT / Power Systems",
    title: "ALAMIN — Smart Power Bus Controller",
    description: "A Bluetooth-controlled power bus system with relay-controlled loads, overcurrent protection, and an HTML dashboard with adjustable amperage thresholds.",
    tags: ["ESP32", "Bluetooth", "Relay Control", "Overcurrent Protection"],
    github: "https://github.com/nshakib22ruet/YourRepoNameHere" }
];
```

- `badge` — short category label shown on the project's detail page
- `title` — shown as the slide name (keep it reasonably short so it fits on one line)
- `description` — the full write-up, only visible on the project's own page
- `tags` — chips shown under the description
- `github` — link to the project's repository

**Behavior note:** as soon as there are 2+ projects, clicking "Projects & Tasks" in the nav (or "Explore Projects" on the hero) will take visitors to the slide list instead of jumping straight into one project — this switch is automatic, you don't need to change anything else.

---

## 4. Editing or adding Contact info

Your contact details currently appear in **three places** — update all of them together to keep things consistent:

1. **Hero section icons** (top of the page) — search for `mailto:` and `github.com/nshakib22ruet` near the top of the `<body>`.
2. **CV page → Personal Information table** — search for `<h3>Personal Information</h3>`, just below it is a table with Email, Phone, GitHub, LinkedIn.
3. **Contact page table** — search for `<div class="eyebrow"><span class="tag">&sect;06</span><h2>Contact Me</h2>`, just below it is a table with the same channels plus Present/Permanent address.

Example — updating your email everywhere: search for `nshakib22ruet@gmail.com` in the file — it will appear a few times (once per `mailto:` link and once as visible text). Replace all occurrences with your new email.

To **add a new contact channel** (e.g. WhatsApp, Twitter/X), add a new row to the Contact page table:

```html
<tr><td>WhatsApp</td><td><a href="https://wa.me/8801XXXXXXXXX" target="_blank">+880 1XX-XXXXXXX</a></td></tr>
```

And, optionally, a matching icon button in the hero section's social bar:

```html
<a href="https://wa.me/8801XXXXXXXXX" target="_blank" class="icon-btn" title="WhatsApp"><i class="fa-brands fa-whatsapp"></i></a>
```

---

## 5. Changing your profile picture

1. Add your new photo file to the same folder as `index.html` (e.g. `profile2.jpg`).
2. Search for `src="profile.jpg"` in `index.html`.
3. Change it to your new filename:

```html
<img src="profile2.jpg" alt="Md. Najmus Shakib" class="profile-img">
```

Tip: a square image (roughly 500×500px or larger) looks best since it's cropped into a circle.

---

## 6. Changing/uploading your CV

1. Replace the file `MdNajmusShakib_CV.pdf` in the repo with your updated PDF (keep the exact same filename, or update the two references below if you rename it).
2. Search for `MdNajmusShakib_CV.pdf` in `index.html` — it appears once, in the CV page's download button:

```html
<a href="MdNajmusShakib_CV.pdf" download="MdNajmusShakib_CV.pdf" class="btn btn-primary">
  <i class="fa-solid fa-file-pdf"></i> Download CV (PDF)
</a>
```

If you rename the PDF file, update **both** the `href="..."` and `download="..."` values to match the new filename.

---

## 7. Changing your "present class" / academic standing

Your current year/standing shows up in **two places**:

1. **Hero stats** (top of page, the "3rd Yr" box) — search for `<div class="stat-value">3rd Yr</div>`:

```html
<div><div class="stat-value">3rd Yr</div><div class="stat-label">Standing</div></div>
```
Change `3rd Yr` to whatever's current (e.g. `4th Yr`, `Final Yr`).

2. **CV page → Education section** — search for `<h3>Education</h3>`, just below it:

```html
<div class="role-title">Bachelor of Science in Engineering (B.Sc. Eng.)</div>
<div class="sub">EEE &middot; RUET &middot; Session 2022–2023 &middot; 3rd Year &middot; Expected Graduation: December 2027</div>
```
Update `3rd Year` and the expected graduation date as needed.

---

## 8. Publishing changes (GitHub Pages)

If this repo is already connected to GitHub Pages:

1. Save your edits to `index.html` (and any new images/PDF).
2. Commit and push to the branch GitHub Pages serves from (usually `main`).
3. Wait ~1 minute, then refresh your live site — changes go live automatically, no extra build step needed.

---

## Quick checklist before pushing

- [ ] Every new item in `skillsData` / `projectsData` ends its object with `}` and has a comma before the next one (except the very last item)
- [ ] Quotation marks are straight `"..."`, not curly `“...”` (curly quotes will break the code)
- [ ] New image/PDF files are actually uploaded to the same repo folder as `index.html`
- [ ] Filenames in the code exactly match the uploaded file names, including capitalization
