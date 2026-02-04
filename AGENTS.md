# Sound Technology Inc Website - Agent Guide

This repository hosts the static website for Sound Technology Inc. This document serves as the authoritative guide for AI agents and developers working on this codebase. Adhere strictly to these guidelines to maintain consistency and functionality.

## 1. Project Overview & Environment

- **Type:** Static Website (HTML5, CSS3, JavaScript).
- **Core Technology:**
  - **HTML:** Semantic structure.
  - **CSS:** Custom styling with CSS Variables (`css/main.css`).
  - **JavaScript:** jQuery-based logic (`js/script.js`).
- **Dependencies (in `resources/`):**
  - jQuery (v3.5.1)
  - Owl Carousel 2 (Sliders/Carousels)
  - Magnific Popup (Lightboxes/Modals)
  - WOW.js (Scroll animations)
  - Animate.css (Animation library)
  - Font Awesome (Icons)

## 2. Development Workflow

Since this is a static site without a package manager (like npm) or build system (like Webpack), the workflow is manual.

### Running the Application
There is no `npm start`. serve the files using a static file server to avoid CORS issues with local file access (especially for fonts and icons).

**Commands:**
```bash
# Python 3
python -m http.server 8000

# Node.js (if available)
npx http-server .
```
*Access:* `http://localhost:8000`

### Build & Linting
- **Build:** None. Source files are served directly. Do not introduce compilation steps (Sass, TS) unless explicitly requested.
- **Linting:** Manual. Ensure:
  - Valid HTML structure (closed tags).
  - CSS syntax validity.
  - No console errors in the browser DevTools.

### Testing Strategy
**Command:** N/A (Manual Verification)

**Procedure for Agents:**
1.  **Visual Check:** After modifying `index.html` or `main.css`, verify the layout on Desktop (>1200px), Tablet (768px-992px), and Mobile (<768px).
2.  **Interactive Check:** Test JavaScript functionality:
    - Navbar Toggler (Mobile).
    - Sticky Navbar on scroll.
    - Carousel navigation (Team/Testimonials).
    - FAQ Accordion expand/collapse.
    - Contact Form inputs.
3.  **Console Check:** Ensure no 404s for assets or JS errors appear in the console.

## 3. Code Style & Conventions

### General Formatting
- **HTML:** 2 spaces indentation.
- **CSS:** 2 spaces indentation.
- **JavaScript:** 4 spaces indentation.
- **Line Endings:** LF or CRLF (consistent with existing file).
- **File Encoding:** UTF-8.

### HTML (`index.html`)
- **Structure:** Use semantic tags: `<header>`, `<nav>`, `<section>`, `<footer>`.
- **IDs & Classes:** Use **kebab-case** (e.g., `feature-left`, `navbar-toggler`).
- **Comments:** Use comments to clearly demarcate start/end of sections.
  ```html
  <!-- about section -->
  <section class="feature" id="about">
    ...
  </section>
  <!-- end of features section -->
  ```
- **Attributes:** Use double quotes `class="container"`.
- **Assets:** Use relative paths (e.g., `assets/img.png`, `resources/lib/style.css`).

### CSS (`css/main.css`)
- **Variables:** Use CSS variables defined in `:root` for colors.
  ```css
  :root {
    --mount-meadow: #1bbc9c; /* Primary Green */
    --night-rider: #343434; /* Dark Grey */
    --white-smoke: #f0f0f0; /* Light Grey */
    --transition: all 0.5s ease-in-out;
  }
  ```
- **Selectors:** Keep selectors low-specificity where possible.
- **Organization:** Group styles by component/section. Media queries go at the **bottom** of the file.
- **Media Queries:** Standard breakpoints:
  - `min-width: 768px` (Tablets)
  - `min-width: 992px` (Desktops)
  - `min-width: 1200px` (Large Screens)

### JavaScript (`js/script.js`)
- **Library:** Use jQuery syntax (`$`) for DOM selection and event handling.
- **Structure:** Wrap all code in `$(document).ready(...)`.
- **Variables:** Use `let` and `const`. Avoid `var`.
- **Strings:** Prefer single quotes `'text'` unless nesting requires double quotes.
- **Event Handlers:**
  ```javascript
  // Good
  $('.toggleMe').click(function(){
      $('.navbar-collapse').slideToggle(400);
  });
  ```
- **Naming:** CamelCase for variables/functions (e.g., `showFaqContent`).

## 4. Library Specifics

### WOW.js & Animate.css
- Elements animate on scroll.
- **Usage:** Add class `wow` and specific animation class (e.g., `animate__fadeInUp`).
- **Configuration:** Initialized in `script.js`.
  ```html
  <div class="wow animate__animated animate__fadeInUp animate__slow">...</div>
  ```

### Owl Carousel
- Used for "Team" and "Testimonials".
- **Configuration:** Defined in `script.js`. Do not modify library files.
- **Responsive Settings:** Check `responsive` object in JS config for breakpoint behavior.

### Magnific Popup
- Used for Video Popup.
- **Class:** `.popup-youtube`.
- **Type:** `iframe`.

## 5. File System Operations
- **Paths:** ALWAYS use **Absolute Paths** when using agent tools to read/write files.
  - Example: `E:\Master Projects\CompletedProjects\Sound Technology Inc v3\Sound Technology Inc\css\main.css`
- **Modifications:** 
  - Prefer `edit` tool for small changes.
  - Use `write` only when creating new files or replacing entire file content is safer.
- **Images:** New images go to `assets/`.
- **Resources:** Do not touch `resources/` unless upgrading a library (rare).

## 6. Common Tasks

**Adding a New Section:**
1.  Create HTML structure in `index.html`.
2.  Add comment headers/footers.
3.  Add corresponding styles in `css/main.css` before media queries.
4.  Add Responsive adjustments in `css/main.css` under appropriate media queries.
5.  If interactive, add logic to `js/script.js`.

**Updating Colors:**
1.  Modify the variable in `:root` in `css/main.css`.
2.  Check for hardcoded overrides (though rare).

**Fixing Layout Issues:**
1.  Check Media Queries at the bottom of `css/main.css`.
2.  Use standard flexbox/grid utilities found in `main.css` (e.g., `.center`, `.row`).

## 7. Version Control Rules
- **Commits:** Write concise, descriptive commit messages (e.g., "fix: navbar alignment on mobile", "feat: add services section").
- **Files:** Do not commit `node_modules` or system files (though none should exist here).
