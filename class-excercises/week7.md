# Week 7 – In-Class Exercise: HTML Page with Express

**Related content:** HTML chapter (document structure, elements, serving with Express)

---

## Objective

Create a valid HTML5 page that matches the layout and content below, then serve it with an Express server so you can view it in the browser at `http://localhost:8080`.

---

## Part 1: Set Up the Express Server

1. Create a folder (e.g. `week7-html-exercise`).
2. Run `npm init` (defaults are fine) and `npm install express`.
3. Create `server.js` that:
   - Uses Express.
   - Listens on port `8080` (or `process.env.PORT || 8080`).
   - Serves your HTML file on the default route `"/"` using `res.sendFile()` and `path.join(__dirname, "views", "index.html")`.
4. Create a `views` folder and put your HTML file there as `index.html`.

---

## Part 2: Build the HTML Page

Your page must be a **valid HTML5 document** and should look like the layout described below. Implement this **in HTML** (structure and semantics); styling is minimal for this exercise.

### How It Should Look (you implement this in HTML)

- **Browser title (tab):** `Week 7 – My Page`

- **Main content structure:**
  - One **main heading** (`<h1>`) at the top: **Welcome to My Page**
  - A short **paragraph** under it: *“This page was built with HTML5 and served with Express.”* Use `<em>` for emphasis where it makes sense.

- **Section: About This Exercise**
  - A **subheading** (`<h2>`): **About This Exercise**
  - A **paragraph** explaining in 1–2 sentences what you did (e.g. created an HTML page and served it with Express). Include at least one **strong** word or phrase using `<strong>`.

- **Section: What We Used**
  - A **subheading** (`<h2>`): **What We Used**
  - An **unordered list** (`<ul>` / `<li>`) with exactly these items:
    - HTML5 document structure
    - Express server
    - The `views` folder for the HTML file

- **Section: Quick Reference**
  - A **subheading** (`<h2>`): **Quick Reference**
  - A **paragraph** that says: *“For more on HTML, see the* [MDN HTML guide](https://developer.mozilla.org/en-US/docs/Web/HTML).*”* Use an anchor tag `<a>` with `href` and `target="_blank"` (and optionally `rel="noopener noreferrer"`).

- **Footer**
  - A **footer** at the bottom with a single line: *“Week 7 – WEB700”* (use a semantic element such as `<footer>`).

---

## Part 3: Checklist (HTML)

Before you finish, confirm:

- [ ] `<!DOCTYPE html>`, `<html>`, `<head>`, `<body>` are present.
- [ ] `<meta charset="utf-8">` and `<title>` are in `<head>`.
- [ ] You used at least: `<h1>`, `<h2>`, `<p>`, `<ul>`/`<li>`, `<a>`, `<em>`, `<strong>`, and a semantic block such as `<footer>` (or `<main>`/`<section>` if you like).
- [ ] The Express server serves `views/index.html` on `"/"`.
- [ ] Running `node server.js` and opening `http://localhost:8080` shows your page with the title, headings, paragraphs, list, link, and footer as described above.

---

## Optional (if time permits)

- Add a **table** with two columns (e.g. “Topic” and “Description”) and 2–3 rows about HTML and Express.
- Validate your HTML at [https://validator.w3.org/](https://validator.w3.org/) or [https://html5.validator.nu/](https://html5.validator.nu/) and fix any reported errors.

---

Run `node server.js`, open `http://localhost:8080`, and confirm the page matches the layout and content described above.
