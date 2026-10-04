# Ariel Zinger — Portfolio

**Live site: [arielzin33-creator.github.io](https://arielzin33-creator.github.io)**

Portfolio of a **Technical Project Manager for AI and software products**: 10+ years leading R&D projects and teams from lab to industrial scale, now with hands-on full-stack and AI engineering.

## What's on the site

- **Experience:** three R&D roles across deep-tech materials and regulated medical products
- **Projects:** five case studies, each structured as *problem → scope & plan → my role → key decision & risk → outcome*
- **Skills:** project management, product & specs, AI & agents, technical fluency
- **Resume:** [download the PDF](https://arielzin33-creator.github.io/assets/resume.pdf)

## Projects

| Project | Case study | Repository |
|---|---|---|
| HALIS — concept to pilot-ready | [#project-4](https://arielzin33-creator.github.io/#project-4) | private |
| biz2code — stage-gate workflow | [#project-2](https://arielzin33-creator.github.io/#project-2) | [biz2code-v3](https://github.com/arielzin33-creator/biz2code-v3) |
| CirqHub — four-day hackathon delivery | [#project-1](https://arielzin33-creator.github.io/#project-1) | [cirqhub](https://github.com/arielzin33-creator/cirqhub) |
| TrueTap — product definition | [#project-5](https://arielzin33-creator.github.io/#project-5) | [truetap](https://github.com/arielzin33-creator/truetap) |
| Mythic Atlas — fixed scope, delivered complete | [#project-3](https://arielzin33-creator.github.io/#project-3) | [mythic-atlas](https://github.com/arielzin33-creator/mythic-atlas) |

## How it's built

A single page in plain HTML and CSS, with no JavaScript, build step or dependencies, served by GitHub Pages. Theme toggle, mobile menu and project modals all use CSS state (`:has()`, `:target`, `<details>`).

```
index.html          the whole page
css/style.css       layout, components, light/dark themes
css/animations.css  motion, reduced-motion safe
assets/             photo, project images, resume.pdf, favicons
```

To preview locally, open `index.html` or run `python -m http.server` in this folder.
