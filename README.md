# Hy-Vee UTM Generator

An internal tool for the Hy-Vee digital marketing team to build consistent,
campaign-tagged tracking URLs. Pick a platform and placement, paste in a base
URL, and the app fills in the right UTM parameters.

## What it does

- Dependent **Platform → Placement** dropdowns
- Applies the correct `utm_source` / `utm_medium` / `utm_campaign` for each
  placement (the mapping is fixed and lives in one spot; see below)
- Optional **Content** parameter for A/B version testing
- Live URL preview with a parameter breakdown
- One-click **Copy** (or press **Enter**)
- **Base URL validation** — must start with `https://` and be a real domain

## How to use

1. Select a **Platform**, then a **Placement**.
2. If prompted, enter a **Campaign Value**.
3. *(Optional)* Add a **Content** value for version testing.
4. Enter the **Base URL** (must start with `https://`).
5. Click **Copy URL** (or press **Enter**).

## Project structure

| File / folder | What it is |
|---|---|
| `index.html` | Markup + the UTM logic (written in Python via Brython) + a little JS for UI polish |
| `styles.css` | All styling |
| `assets/` | Hy-Vee logos, favicon, and the celebration sound |

## Editing the UTM mapping

The parameter mapping lives in the `utm_mapping` dictionary near the top of the
`<script type="text/python">` block in `index.html`. Each **platform → placement**
maps to `{source, medium, campaign}`. To add or change placements, edit that
dictionary. A `campaign` value of `'content'` means the user is asked to type a
custom campaign name.

## Running it locally

The app must be served over **HTTP** for Brython (the Python-in-the-browser
engine) to run — opening `index.html` directly with `file://` will not work.

```bash
py -m http.server 8777
```

Then open <http://localhost:8777>.

## A note on the CSS version number

`styles.css` is linked as `styles.css?v=9`. That `?v=N` is a cache-buster, not
real version control. Bump the number whenever you change the CSS so browsers
load the new file instead of a cached copy.

## Ownership

Internal Hy-Vee tool. The logos and audio are Hy-Vee property; keep hosting
appropriate for internal use.

<details>
<summary>Hidden extras (spoilers)</summary>

A few easter eggs for the team, none of which affect the default experience:

- **Double-click the "Digital Marketing" subtitle** → a Hy-Vee employee pushes a
  produce cart across the bottom of the screen (silent). Click him mid-walk and
  he waves.
- **Triple-click the Hy-Vee logo** → the tagline rains down the screen with the
  jingle.
- **Konami code** (↑ ↑ ↓ ↓ ← → ← → B A) → a whole parade of carts.

</details>
