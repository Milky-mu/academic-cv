# Custom icons — university emblems

These render in the circle on each education/experience entry, LinkedIn-style,
in place of the default graduation-cap.

## Installed

| File | University | Source | Licence | Size |
|---|---|---|---|---|
| `tsinghua.svg` | Tsinghua University | [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Tsinghua_University_Logo.svg) | **Public domain** | 276 KB |
| `sun-yat-sen.svg` | Sun Yat-sen University | [zh.wikipedia](https://zh.wikipedia.org/wiki/File:Sun_Yat-sen_Univ_Logo.svg) | 合理使用 / fair use — **copyrighted** | 36 KB |
| `northwest-af.svg` | Northwest A&F University | [zh.wikipedia](https://zh.wikipedia.org/wiki/File:Northwest_A%26F_University.svg) | 合理使用 / fair use — **copyrighted** | 86 KB |

Referenced from `data/authors/me.yaml` as `icon: custom/tsinghua` etc.

### On the licences

Two of these are uploaded to Wikipedia under a *fair use* rationale, not a free
licence. Showing your alma mater's emblem on your own CV page is nominative use
— the same thing LinkedIn does — and is normal practice. But it is not
free-licensed material, so: use the marks unmodified, don't recolour them, and
don't imply endorsement. If you'd rather not, delete the file and comment out
the matching `icon:` line and you get the clean graduation-cap back.

### On the file sizes

These are inlined into the HTML, on both the homepage and `/experience/`.
They were optimised by rounding path coordinates to 0.1 units — on a 267-unit
viewBox that's a worst-case 0.009 px error at 48 px, i.e. invisible. Tsinghua's
is still large (276 KB from 423 KB) because it's a detail-traced seal; it
compresses well over the wire but if page weight bothers you, replacing it with
a simplified official mark is the fix.

## Adding another

1. Save as **`<name>.svg`** here (SVG only — PNG/JPG are not resolved)
2. Reference it as **`icon: custom/<name>`** in `data/authors/me.yaml`

Constraints:

- **Renders at 24px** inside a 48px circle. Detailed crests get muddy — prefer
  the simplified shield or monogram most universities publish for small use.
- **Colour**: the SVG keeps its own `fill` values. One using `currentColor`
  gets tinted with your site accent, which usually looks wrong for a logo.
- **A missing file renders the Hugo logo**, not a fallback cap. Add the file
  before uncommenting the `icon:` line.

## If 24px is too small

The size is set in the theme's block template. It can be overridden with a
targeted CSS rule in `layouts/_partials/hooks/head-end/`. Worth doing *after*
the first deploy, so the rule can be checked against the real page rather than
guessed — ask and it can be added.
