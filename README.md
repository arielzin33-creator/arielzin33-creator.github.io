# Developer Portfolio + GitHub Profile README

Two matching pieces:

1. **`index.html`** — a single-page portfolio built with **pure HTML + CSS**. No
   JavaScript, no build step, no dependencies.
2. **`profile-readme/`** — a GitHub **profile README** for your special
   `Username/Username` repository, carrying the same sections in Markdown.

They cross-link: the README's Portfolio badge points at the site, and the site's Stats
section points back at the README.

## What's included — portfolio site

| Requirement | Where it lives |
|---|---|
| Profile picture | Hero section — animated conic ring around the avatar |
| Bio / "about me" | Hero short bio + `#about` long bio with stat cards |
| Skills & languages | `#skills` — animated proficiency bars, grouped chips, shields.io badge wall |
| Education & certificates | `#resume` → **Academics** accordion, timeline that draws itself on scroll |
| Work experience | `#resume` → **Experience** accordion |
| Coding handles | `#resume` → **Coding handles** accordion (LeetCode, Codeforces, GFG, HackerRank) |
| GitHub & LinkedIn links | Hero social icons, contact aside, and footer |
| Resume download button | Hero CTA and contact aside → `assets/resume.pdf` |
| Projects | `#projects` — cards that open full case-study modals |
| Stats & activity | `#stats` — GitHub stat cards, trophies, snake graph, recent activity, joke/quote |
| Contact form | `#contact` — floating labels, validation, spam honeypot |
| Transitions & animations | `css/animations.css` — all of it, reduced-motion safe |

Each project modal answers the five required questions: why you built it, what tools you
used and how long it took, what challenged you, what you learned — plus **GitHub repo**
and **live demo** buttons and a screenshot gallery.

## Files

```
portfolio/
├── index.html                  ← all site content; the main file you edit
├── css/
│   ├── style.css               ← design tokens, layout, components
│   └── animations.css          ← keyframes + scroll-driven reveals
├── assets/
│   ├── profile.svg             ← replace with your photo
│   ├── favicon.svg
│   ├── resume.pdf              ← ADD THIS (see below)
│   └── projects/
│       ├── project-1.svg       ← replace with real screenshots
│       ├── project-2.svg
│       └── project-3.svg
└── profile-readme/             ← for github.com/YourUsername/YourUsername
    ├── README.md               ← the profile README itself
    ├── SETUP.md                ← how to deploy it + wire up the Actions
    ├── icons/README.md         ← which icon files to add, and where to get them
    └── .github/workflows/
        ├── snake.yml           ← contribution-graph snake animation
        └── activity.yml        ← auto-updating recent-activity list
```

## Customise it — in order

1. **Search `index.html` for `EDIT:`.** Every spot that needs your details is marked.
2. **Name, bio, job title.** Hero section. Change the four rotating roles in `.roles__list`
   (keep the last `<li>` a copy of the first so the loop is seamless).
3. **Photo.** Replace `assets/profile.svg` with a square image (~600×600) and update the
   `<img src>` and `alt`.
4. **Resume.** Export your CV as PDF and save it as `assets/resume.pdf`.
5. **Links.** Replace every `your-username`, `your-handle` and `you@example.com`.
6. **Skills.** Each bar's level is one number: `style="--level: 85%"` — change that and the
   `%` label next to it.
7. **Education & experience.** One `<li class="timeline__item">` per entry, inside the
   matching `<details class="acc">` accordion.
8. **Coding handles.** Update the four `.handle` links, or delete the platforms you
   don't use.
9. **Stats section.** Replace `your-username` in every card URL — until you do, the
   cards render as empty frames showing their alt text. Same for `your-handle` on the
   LeetCode and Codeforces cards.
10. **Projects.** Each project is a `<a class="card" href="#project-N">` in the grid plus a
    matching `<article class="modal" id="project-N">` at the bottom of the file. Copy both,
    bump the number, and they're wired together automatically.
11. **Contact form.** GitHub Pages can't process form posts, so point the form at a free
    relay — sign up at [Formspree](https://formspree.io), then replace `YOUR_FORM_ID` in
    the `action` attribute. ([Web3Forms](https://web3forms.com) and
    [Getform](https://getform.io) work the same way.)
12. **Colours.** Three lines at the top of `style.css`:

    ```css
    --accent:   #7c5cff;
    --accent-2: #22d3ee;
    --accent-3: #f472b6;
    ```

    Everything else — buttons, bars, glows, the light theme — derives from those.

## How the no-JavaScript tricks work

- **Light/dark toggle** — a hidden checkbox at the top of `<body>`; the whole page reacts
  through `:root:has(#theme-toggle:checked)`, which swaps the colour tokens.
- **Mobile menu** — same pattern with a second checkbox.
- **Project modals** — each modal is hidden until its `id` matches the URL fragment, using
  the `:target` selector. Clicking a card sets the fragment; the close button and the
  backdrop link back to `#projects`.
- **Collapsible sections** — native `<details>`/`<summary>`, mirroring the README's
  structure. The chevron rotates with a CSS transform; the panel content fades in with a
  keyframe, since `<details>` can't transition its own height.
- **Scroll animations** — CSS scroll-driven animations (`animation-timeline: view()`),
  wrapped in `@supports` so older browsers just show the content instead of a blank page.
- **Rotating job titles** — a list that slides vertically inside an `overflow: hidden` box.

## Browser support

Works everywhere. Chrome/Edge 115+ and Safari 26+ get the scroll-reveal animations;
Firefox (as of writing) renders everything without them, which is the intended fallback.
`:has()` is supported in all current browsers — in anything older the page stays in dark
mode and the mobile menu doesn't open, so keep the desktop nav in mind if you must
support very old browsers.

Everything respects `prefers-reduced-motion: reduce` — all animation stops.

## Deploy to GitHub Pages

```bash
git init
git add .
git commit -m "Add portfolio"
git branch -M main
git remote add origin https://github.com/your-username/your-username.github.io.git
git push -u origin main
```

Then: repo → **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`**.

Naming the repo `your-username.github.io` publishes it at
`https://your-username.github.io`. Any other repo name publishes at
`https://your-username.github.io/repo-name/` — the template uses relative paths, so both
work without changes.

## The GitHub profile README

See [`profile-readme/SETUP.md`](profile-readme/SETUP.md) for the full walkthrough. Short
version: create a public repo named exactly your username, copy `README.md`, `icons/`
and `.github/workflows/` into it, find-and-replace the placeholders, then set
**Settings → Actions → Workflow permissions → Read and write** so the snake and activity
workflows can commit back.

Two corrections to the widely-copied snippets, both already applied here:

- `github-readme-streak-stats.herokuapp.com` is dead (Heroku dropped its free tier) —
  the maintained host is `streak-stats.demolab.com`.
- `github.com/user/repo/blob/main/icons/x.gif` serves an HTML page, not the image. Use
  `raw.githubusercontent.com/user/repo/main/icons/x.gif` or append `?raw=true`.

## Before you share the link

- [ ] Every `your-username` / `your-handle` / `you@example.com` placeholder replaced
      (they appear in the stats cards and coding handles too)
- [V ] `assets/resume.pdf` exists and opens
- [ ] Contact form endpoint set, and you sent yourself a test message
- [ ] Real screenshots in `assets/projects/`
- [ ] `<title>`, meta description and `og:image` updated
- [ ] Stats cards actually render — if a card is blank, that third-party service is down
- [ ] Checked at 375 px wide, and tabbed through the page with the keyboard only
