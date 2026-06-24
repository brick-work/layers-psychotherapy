# Project Notes — Layers Psychotherapy Website

## Still to do

- Replace `[ photo ]` in `about.html` with a real headshot
- Update the email address in `contact.html` with your actual email
- Review and edit all copy to match your voice exactly

Full checklist also lives in [TODO.md](TODO.md).

---

## How HTML and CSS work together

A website is made of two types of files working as a team:

- **HTML files** (`.html`) define the *content and structure* of each page — the text, headings, buttons, forms, and how things are arranged.
- **CSS files** (`.css`) define the *appearance* of that content — colors, fonts, spacing, and layout.

In this project, all four pages share a single stylesheet called `shared.css`. Each HTML file has one line near the top that links to it:

```html
<link rel="stylesheet" href="shared.css" />
```

This means if you want to change a font, color, or spacing across the whole site, you only edit `shared.css` once and all four pages update automatically. If the styles were instead written inside each individual HTML file, you'd have to make the same change in four places every time.

---

## What we built today

### Step 1 — Decided on the basics
- Practice name: **Layers Psychotherapy**
- Feel: clean and professional
- Pages needed: Home, About, Services, Contact

### Step 2 — Built the initial site
Created a single `index.html` file containing all four sections stacked on one scrolling page, with a fixed navigation bar at the top.

### Step 3 — Split into separate pages
At your request, broke the single file into four separate pages:

| File | Page |
|---|---|
| `index.html` | Home (hero / landing) |
| `about.html` | About Jack Hambrick, MFT |
| `services.html` | Services + How We Work |
| `contact.html` | Contact form |

All shared styles were moved into `shared.css` so they wouldn't need to be repeated in every file.

### Step 4 — Combined Services and How We Work
Merged the "How we work" section (the numbered 01 / 02 / 03 intake → framework → work breakdown) directly into `services.html` beneath the three service cards, since they belong together.

### Step 5 — Added this notes file
Created `NOTES.md` (this file) in the root folder to document the project structure and the steps taken.

---

## Files in this folder

```
index.html       — Home page
about.html       — About page
services.html    — Services + How We Work page
contact.html     — Contact page
shared.css       — All styles, shared across every page
NOTES.md         — This file
```

