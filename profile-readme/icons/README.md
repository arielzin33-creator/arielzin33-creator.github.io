# /icons

Push this folder to the **main branch** of your profile repository
(`github.com/YourUsername/YourUsername`). The README references each file at:

```
https://raw.githubusercontent.com/YourUsername/YourUsername/main/icons/<filename>
```

> The brief's snippets use `github.com/.../blob/main/icons/...`. A `blob` URL
> serves an HTML page rather than the file, so it often renders as a broken
> image. Use `raw.githubusercontent.com` (as above) or append `?raw=true`.

## Files the README expects

| Filename | Used for | Suggested size |
|---|---|---|
| `Hi.gif` | waving hand next to the greeting | 28 px |
| `about.gif` | About Me heading | 37 px |
| `about.png` | Résumé heading | 37 px |
| `academics.gif` | Academics sub-section | 29 px |
| `experience.gif` | Experience sub-section | 29 px |
| `techstack.gif` | Tech Stack sub-section | 29 px |
| `projects.gif` | Projects sub-section | 29 px |
| `stats.gif` | Stats heading | 32 px |
| `activity.gif` | Recent Activity heading | 25 px |
| `Contact.gif` | Contact Me heading | 37 px |
| `Gmail.gif` | clickable email button | 100 px |

## Where to get the animated section icons

- **[Giphy](https://giphy.com/)** — download as GIF, keep them small (under ~200 KB each)
- **[Icons8 animated icons](https://icons8.com/animated-icons)** — free with attribution
- **[LottieFiles](https://lottiefiles.com/)** — export a Lottie animation to GIF

## Where to get social / tech-stack icons

The README's badge rows (`img.shields.io`) already cover most brand logos. If
you want actual icon *images* instead — e.g. for a social-links row of your
own, styled with the snippet in [`../SETUP.md`](../SETUP.md#custom-image-snippet) —
these are the four go-to sources:

| Source | Style | License / credit |
|---|---|---|
| **[Simple Icons](https://simpleicons.org/)** | flat, single-colour brand marks | Free, open source (CC0) — no credit required. Start here. |
| **[Wikimedia Commons](https://commons.wikimedia.org/wiki/Main_Page)** | official brand logos | Free, mostly public domain / CC — check each file's licence page |
| **[Flaticon](https://www.flaticon.com/)** | illustrated, many art styles | Free tier requires crediting the individual artist; premium removes that |
| **[Icons8](https://icons8.com/)** | illustrated + animated | Same as Flaticon — free tier needs an attribution link back to Icons8 |

Simple Icons and Wikimedia Commons need no attribution. Flaticon and Icons8
are made by individual designers — read the licence on the specific icon page
before using it without a credit link.

## Don't want to host icons?

Every `<img>` in the README has a fallback emoji noted in an HTML comment
beside it. Delete the `<img>` tag and keep the emoji — the layout is unchanged
and nothing can break.

Keep total folder size small. GitHub caches these through its image proxy, but
a 5 MB GIF still makes your profile feel slow on mobile.
