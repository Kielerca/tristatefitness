# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static marketing site for Tristate Fitness (tristatefitclub.com), built from the HTML Codex "Gym" Bootstrap 5 template. There is no build step, package manager, linter, or test suite. The `CNAME` file indicates GitHub Pages hosting from `main`, so pushing to `main` deploys.

## Local preview

Serve the repo root with any static server and open the page:

```sh
python3 -m http.server 8000
```

## Architecture

- Each page (`index.html`, `about.html`, `class.html`, `team.html`, `blog.html`, `testimonial.html`, `contact.html`, `dispensary.html`) is a standalone HTML file. The `<head>`, navbar, and footer are duplicated in every page, so a nav or footer change must be applied to each file by hand. Nav labels differ from filenames: `class.html` is "Services" and `blog.html` is "Photos".
- `success.html` is a minimal standalone page with no navbar.
- Membership signup, class booking, and the member portal are external links to GymMaster (`tristatefitness.gymmasteronline.com`). The site has no forms or backend of its own.
- `index.html` also loads Google Analytics (gtag) and LogRocket.

## Styling

- `css/bootstrap.min.css` is a precompiled Bootstrap build with brand colors baked in (`$primary: #2a338f`, fonts Oswald/Rubik). Its source is `scss/bootstrap.scss`, but no compile tooling exists in the repo. Changing brand variables requires compiling the SCSS externally and replacing `css/bootstrap.min.css`.
- `css/style.css` holds template overrides and mirrors the brand colors as CSS custom properties on `:root`. Put custom styles here.
- `css/disp.css` is not referenced by any page.

## JavaScript

`js/main.js` wires jQuery plugins from `lib/` (easing, waypoints, counterup, owlcarousel): hover dropdowns above 992px, back-to-top button, `[data-toggle="counter-up"]` counters, and `.testimonial-carousel`. jQuery 3.4.1 and the Bootstrap 5.0 bundle load from CDNs at the bottom of each page.
