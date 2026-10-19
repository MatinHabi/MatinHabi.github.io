<!--
  README layout notes (so you can reuse this style elsewhere):
  - The <div align="center"> block centres the title and badges on GitHub.
  - Badges come from shields.io. The URL format is:
      https://img.shields.io/badge/<LABEL>-<COLOUR HEX>?style=flat-square&logo=<LOGO NAME>&logoColor=white
  - HTML comments like this one are hidden when GitHub renders the README.
-->

<div align="center">

# Matin Habibian — Portfolio Website

A personal portfolio site built from scratch with plain HTML, CSS and JavaScript.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)

[Live site]([placeholder: live URL]) · [GitHub](https://github.com/MatinHabi) · [LinkedIn](https://www.linkedin.com/in/matin-habibian-631055339/)

</div>

---

## Contents

1. [What it is](#what-it-is)
2. [How it works](#how-it-works)
3. [Data and inputs](#data-and-inputs)
4. [How to run it](#how-to-run-it)
5. [Project structure](#project-structure)
6. [Results](#results)
7. [Notes and known issues](#notes-and-known-issues)

---

## What it is

A single-page portfolio for **Matin Habibian**. Matin is a Bachelor of Computer Science student at **Adelaide University** (formerly The University of Adelaide), majoring in **Artificial Intelligence and Machine Learning**, with an expected graduation of **July 2027**.

The page has two columns:

| Left column (blue panel) | Right column (white) |
| --- | --- |
| Profile photo | Experience and leadership |
| Short "About me" | Education and certification |
| GitHub, LinkedIn and resume-download buttons | Projects, each with a button linking to the project |

Each section fades and slides into view as you scroll.

No frameworks, build tools or libraries are used. The only external resource is Google Fonts.

---

## How it works

### 1. Two-column layout (Flexbox)

`.page_wrapper` is a flex container that holds the two columns side by side:

```css
.page_wrapper { display: flex; min-height: 100vh; }
.left_side    { flex: 0 0 35%; }   /* fixed at 35% of the width */
.right_side   { flex: 1; }         /* takes up whatever space is left */
```

The left panel uses a blue `linear-gradient` background. Its right-hand corners are rounded with `border-top-right-radius` and `border-bottom-right-radius`.

### 2. Responsive design (media query)

On screens **768px wide or narrower**, the `@media (max-width: 768px)` block in [style.css](style.css):

- switches the wrapper to `flex-direction: column`, so the blue panel sits on top of the content;
- makes both columns `width: 100%`;
- moves the rounded corners to the bottom of the blue panel;
- makes the contact icons bigger (60px) so they're easier to tap;
- shrinks the section corner radius and centres the `h2` headings.

### 3. Scroll fade-in animation ([script.js](script.js))

Every element with the class `fade-in-section` starts hidden and shifted down:

```css
.fade-in-section         { opacity: 0; transform: translateY(100px); transition: ... 1.5s; }
.fade-in-section.visible { opacity: 1; transform: translateY(0); }
```

JavaScript decides when to add the `visible` class:

- `isInView(element)` uses `getBoundingClientRect()` to check whether the element's top is at least 200px above the bottom of the window and its bottom hasn't scrolled off the top.
- `handleScroll()` loops over every `.fade-in-section`. It **adds** `visible` to sections in view and **removes** it from the rest, so sections fade in again each time you scroll back to them. If the whole page fits in the window, every section is shown.
- `handleScroll()` runs on the `scroll`, `load` and `resize` events.

The CSS `transition` handles the animation itself. The JavaScript only switches a class on or off.

### 4. Nested CSS

Some rules use native CSS nesting, for example:

```css
#experience {
    h3 { font-size: large; }
    h4 { font-weight: normal; }
}
```

This works in current versions of Chrome, Edge, Firefox and Safari, but very old browsers ignore it.

### 5. Links and resume download

- The GitHub, LinkedIn and project buttons use `target="_blank"`, so they open in a new tab.
- The resume button uses the `download` attribute on `<a href="Matin Habibian Resume.pdf">`, so the browser saves the PDF instead of opening it.
- Project buttons are pill-shaped (`border-radius: 350px`) and fade from blue to pink on hover using `transition: background 0.4s`.

---

## Data and inputs

The site has no database, API or form. Everything is hard-coded:

| Input | Where it lives |
| --- | --- |
| About me, experience, leadership, education and project text | Typed directly into [index.html](index.html) |
| Profile photo | `Matin.jpg` |
| Contact icons | `Git-Logo.png`, `LinkedInLogo.png`, `ResumeDownload.png` |
| Downloadable resume | `Matin Habibian Resume.pdf` |
| Fonts | Google Fonts (Montserrat and Lora), loaded in the `<head>` of `index.html` |

To update the content, edit the text in `index.html` and replace the image or PDF files, keeping the same file names.

---

## How to run it

You don't need to install anything.

**Option 1: open the file**

1. Clone or download the repo:
   ```bash
   git clone https://github.com/MatinHabi/matin-website-portfolio.git
   ```
2. Double-click `index.html` to open it in a browser.

**Option 2: run a local server (closer to how a hosted site behaves)**

```bash
cd matin-website-portfolio
python3 -m http.server 8000
```

Then go to <http://localhost:8000> in your browser.

**Hosting:** [placeholder: GitHub Pages, Netlify or another host, plus the live URL. I couldn't tell from the repo whether the site is deployed.]

---

## Project structure

```
matin-website-portfolio/
├── index.html                  # Page content and structure
├── style.css                   # Layout, colours, responsive rules, fade-in styles
├── script.js                   # Scroll detection that adds/removes the "visible" class
├── Matin.jpg                   # Profile photo
├── Git-Logo.png                # GitHub button icon
├── LinkedInLogo.png            # LinkedIn button icon
├── ResumeDownload.png          # Resume download button icon
├── Matin Habibian Resume.pdf   # File downloaded by the resume button
├── README.md
│
│   # The images below are in the repo but not used by any HTML, CSS or JS:
├── EmailLogo.png
├── Phone.png
├── Picture 1.png
├── Pinkpink.png
├── light pink.png
├── yellow.png
└── background_left_side.png
```

---

## Results

| Metric | Desktop | Mobile |
| --- | --- | --- |
| Lighthouse – Performance | [placeholder] | [placeholder] |
| Lighthouse – Accessibility | [placeholder] | [placeholder] |
| Lighthouse – Best Practices | [placeholder] | [placeholder] |
| Lighthouse – SEO | [placeholder] | [placeholder] |

**Screenshots**

| Desktop | Mobile |
| --- | --- |
| [placeholder: desktop screenshot] | [placeholder: mobile screenshot] |

<!-- To get Lighthouse scores: open the site in Chrome → right-click → Inspect → "Lighthouse" tab → Analyse page load. -->

---

## Notes and known issues

These are things I noticed in the code. I've listed them instead of guessing what was intended:

- **`#name` is always hidden.** `#name { display: none; }` applies at every screen width, so the `<h1>Matin Habibian</h1>` heading never appears. It's unclear whether this is on purpose.
- **`#references` no longer exists.** `script.js` still looks for an element with `id="references"`. That section was removed from the HTML, so this code does nothing (and doesn't cause an error).
- **Lora is loaded but not used.** `index.html` loads both Montserrat and Lora, but `style.css` only uses Montserrat.
- **Two CSS values are ignored by browsers.** In `.ProjectButton .btn`, `display: run-in` isn't supported by most browsers, and `background-color: none` isn't valid CSS. Browsers skip both, so the button stays blue (`#0b54fc`).
- **The bundled resume PDF is older than the site text.** `Matin Habibian Resume.pdf` was created in December 2025, before the experience and projects now listed in `index.html`.
