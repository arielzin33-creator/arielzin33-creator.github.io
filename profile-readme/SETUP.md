# Profile README — setup

## 0. Plan before you build

Before touching Markdown, decide what this page is actually for — it's easy
to end up with a wall of badges that says nothing about you. Sketch answers
to these first, even just mentally:

- **Tone**: mostly gifs and colour, or a quieter text-first page?
- **Focus**: is this about *you* (bio, skills, journey) or your *work*
  (pinned repos, projects, stats)? Most good profiles lead with one and use
  the other to back it up.
- **Audience**: recruiters skim for 10 seconds — put your strongest project
  and tech stack above the fold. Other developers read further — that's
  where stats, streaks and jokes earn their space.

The template in this folder leans "text-first, backed by stats" — bio and
résumé near the top, live GitHub data further down. If you want more of a
gif-and-badge showcase instead, that's a legitimate different direction;
just be deliberate about which one you're building.

## 1. Learn the Markdown syntax

The whole README is written in **GitHub Flavored Markdown** — GitHub's
extension of standard Markdown with a few extra features (task lists, tables,
`<details>` panels, emoji shortcodes). If you haven't written much Markdown:

- [Markdown Guide — Basic Syntax](https://www.markdownguide.org/basic-syntax/) —
  the fastest reference for headings, lists, links, and emphasis
- [GitHub Docs — Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) —
  covers the GitHub-specific extensions this README relies on (`<details>`,
  badges via raw HTML, alignment attributes)

You don't need to memorise it — this file's `README.md` already demonstrates
every pattern you're likely to need. Copy from it.

## 2. Create the special repository

GitHub renders `README.md` from a repository named **exactly** your username on
your profile page.

1. New repository → name it `YourUsername` (identical to your handle, case included)
2. Public, and tick **Add a README file**
3. If the name matches, GitHub shows: *"You found a secret! …is a special repository."*

## 3. Copy the files in

From this folder, into the root of that repo:

```
README.md
icons/                    ← your GIFs/PNGs (see icons/README.md)
.github/workflows/snake.yml
.github/workflows/activity.yml
```

```bash
git clone https://github.com/YourUsername/YourUsername.git
cd YourUsername
# copy README.md, icons/ and .github/ in here
git add .
git commit -m "Add profile README"
git push
```

## 4. Find and replace

| Placeholder | Replace with |
|---|---|
| `YourUsername` | your GitHub handle |
| `Your Name` | your display name |
| `your-handle` | LeetCode / Codeforces / LinkedIn handle |
| `your-email@example.com` | your email |

Check the result at `https://github.com/YourUsername` before moving on. Any
broken image is almost always a wrong path in `/icons` or a typo in the handle.

## 5. Turn on the Actions

**Settings → Actions → General → Workflow permissions → Read and write permissions.**
Both workflows commit back to the repo, so they fail without this.

Then **Actions** tab → pick each workflow → **Run workflow** to trigger the first
run instead of waiting for the schedule.

- `snake.yml` publishes `snake.svg` and `snake-dark.svg` to an `output` branch.
  The README's `<picture>` block serves the dark version to dark-mode viewers.
- `activity.yml` rewrites the list between the `START_SECTION:activity` and
  `END_SECTION:activity` comment markers. Keep those markers in place.

For the **Merged PRs** counter, follow
[this walkthrough](https://dev.to/parth_johri/elevate-your-github-profile-with-the-merged-prs-github-action-31ek);
the `Start/Finish Count Merged PRs` and `Start/Finish Merged PRs` markers are
already in the README, ready for it.

## 6. Stat cards

### Reference table

| Card | Host | Notes |
|---|---|---|
| Stats, top languages | `github-readme-stats.vercel.app` | Rate-limited on the public instance. Self-host if cards go blank. |
| Streak | `streak-stats.demolab.com` | **The `github-readme-streak-stats.herokuapp.com` URL in the brief is dead** — Heroku dropped its free tier. Use this host. |
| Activity graph | `github-readme-activity-graph.vercel.app` | |
| Trophies | `github-profile-trophy.vercel.app` | |
| LeetCode | `leetcard.jacoblin.cool` | The brief's `leetcode.card.workers.dev` is unreliable; this is the maintained one. |
| Profile views | `komarev.com/ghpvc` | Counts from the day you add it. |

All of these are third-party services. If your profile ever shows a wall of
broken images, one of them is down — not your fault, and worth a self-hosted
fork if it matters to you.

### The generic github-readme-stats pattern

Every card from [`github-readme-stats`](https://github.com/anuraghazra/github-readme-stats)
follows one URL shape:

```
https://github-readme-stats.vercel.app/api/<CARD_TYPE>/?username=<USERNAME>&theme=<THEME_NAME>
```

`CARD_TYPE` is where the variety lives:

| `CARD_TYPE` | Result |
|---|---|
| *(blank — just `/api/`)* | aggregated user stats (stars, commits, PRs, issues) |
| `top-langs` | your most-used languages, as a compact chart |
| `pin` | a single pinned repository card (needs `&repo=<REPO_NAME>` too) |
| `gist` | a pinned gist card |

`theme` accepts dozens of built-in names (`tokyonight`, `dracula`, `radical`,
`nord`…) — see the [theme gallery](https://github.com/anuraghazra/github-readme-stats/blob/master/themes/README.md) —
or you can hand-pick colours with `&bg_color=&title_color=&text_color=` the
way the portfolio site's `#stats` section does, so the cards match a palette
that isn't in the preset list.

### Showcasing individual repos with `pin`

The stats in this template cover your *activity*, not your *work*. To put
specific repos front and centre — the "Showcase Your Repos" idea — add a
`pin` card per project:

```html
<a href="https://github.com/YourUsername/nomad-desk" target="_blank">
  <img align="center"
       src="https://github-readme-stats.vercel.app/api/pin/?username=YourUsername&repo=nomad-desk&theme=tokyonight"
       height="165" />
</a>
```

Two or three of these, side by side under a `### Pinned Repositories`
heading, does more to show what you've actually built than the aggregate
stats cards do — use both, not one instead of the other.

## 7. Custom image snippet

Anywhere you want to drop in an image or gif that isn't one of the pre-built
cards above — a banner, a personal photo, a project screenshot — this is the
pattern the rest of the README uses, so new additions stay consistent:

```html
<a href="URL_REDIRECT" target="_blank">
  <img align="center" src="URL_TO_YOUR_IMAGE" height="100" />
</a>
```

- `href` — where the image links to. Delete the whole `<a>` wrapper (keep
  just the `<img>`) if it shouldn't be clickable.
- `target="_blank"` — opens the link in a new tab, so visitors don't lose
  your profile.
- `align="center"` — also accepts `"left"` or `"right"`.
- `src` — the image URL. **Upload it to your `icons/` folder and reference it
  with a `raw.githubusercontent.com` URL** rather than linking an external
  host — a URL you don't control can go dead or get swapped out later.
- `height` (or `width`, not usually both) — pin this to the same value across
  a row of images so they line up.

## 8. More cards worth adding

- [WakaTime stats](https://github.com/athul/waka-readme) — time spent per language
- [Metrics](https://github.com/lowlighter/metrics) — a detailed infographic
- [README Terminal](https://github.com/x0rzavi/github-readme-terminal) — animated terminal GIF
- [Profile Header Generator](https://leviarista.github.io/github-profile-header-generator/) — custom banner

## Keeping the two in sync

The portfolio site (`../index.html`) carries the same sections: résumé,
coding handles, tech stack, projects, stats, contact. When you update one,
update the other — the README's Portfolio badge links to the site, and the
site's Stats section links back to the README.
