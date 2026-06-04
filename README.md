# wc26-assets

Public static asset hosting for **FIFA World Cup 2026** creative production.

Served via **GitHub Pages** at:

```
https://sachawd.github.io/wc26-assets/
```

Used by: Airtable · Table-to-Figma · Figma · Campaign Builder

---

> ⚠️ **SECURITY WARNING**
> This is a **public repository**.
> Never commit API keys, `.env` files, secrets, tokens, or credentials of any kind.
> Only commit approved static image assets.

---

## Folder Structure

```
wc26-assets/
├── team-logos/       # National team badge/crest images
│   └── .gitkeep
├── flags/            # Country flag images
│   └── .gitkeep
├── badges/           # Tournament badges and event marks
│   └── .gitkeep
└── README.md
```

---

## Naming Convention

- **Lowercase kebab-case only** — no spaces, no uppercase, no underscores
- **PNG format** preferred (transparent background where applicable)
- **Square format** recommended for logos and badges (e.g. 512×512px)
- Filename must match the team's canonical lowercase English name

### Team Logo Examples

| File | URL |
|------|-----|
| `team-logos/argentina.png` | `https://sachawd.github.io/wc26-assets/team-logos/argentina.png` |
| `team-logos/brazil.png` | `https://sachawd.github.io/wc26-assets/team-logos/brazil.png` |
| `team-logos/canada.png` | `https://sachawd.github.io/wc26-assets/team-logos/canada.png` |
| `team-logos/england.png` | `https://sachawd.github.io/wc26-assets/team-logos/england.png` |
| `team-logos/france.png` | `https://sachawd.github.io/wc26-assets/team-logos/france.png` |
| `team-logos/germany.png` | `https://sachawd.github.io/wc26-assets/team-logos/germany.png` |
| `team-logos/mexico.png` | `https://sachawd.github.io/wc26-assets/team-logos/mexico.png` |
| `team-logos/usa.png` | `https://sachawd.github.io/wc26-assets/team-logos/usa.png` |

### Multi-word Countries

Use a hyphen between words:

| Country | Filename |
|---------|----------|
| South Africa | `south-africa.png` |
| Saudi Arabia | `saudi-arabia.png` |
| South Korea | `south-korea.png` |
| Costa Rica | `costa-rica.png` |
| Bosnia & Herzegovina | `bosnia-and-herzegovina.png` |
| New Zealand | `new-zealand.png` |
| United States | `usa.png` *(use common abbreviation)* |

---

## Public Base URL

```
https://sachawd.github.io/wc26-assets/
```

### URL Pattern

```
https://sachawd.github.io/wc26-assets/{folder}/{filename}.png
```

**Examples:**
```
https://sachawd.github.io/wc26-assets/team-logos/argentina.png
https://sachawd.github.io/wc26-assets/flags/brazil.png
https://sachawd.github.io/wc26-assets/badges/wc26-official.png
```

---

## Airtable Formula — Home Team Logo URL

Use this formula in an Airtable formula field (`Home_Team_Logo_URL`) to auto-generate
the logo URL from the `Home_Team` text field:

```
"https://sachawd.github.io/wc26-assets/team-logos/"
& LOWER(
    SUBSTITUTE(
      SUBSTITUTE(
        SUBSTITUTE({Home_Team}, " & ", "-and-"),
        " ", "-"
      ),
      "'", ""
    )
  )
& ".png"
```

### Away Team Logo URL

```
"https://sachawd.github.io/wc26-assets/team-logos/"
& LOWER(
    SUBSTITUTE(
      SUBSTITUTE(
        SUBSTITUTE({Away_Team}, " & ", "-and-"),
        " ", "-"
      ),
      "'", ""
    )
  )
& ".png"
```

### How It Works

| `Home_Team` field value | Generated URL |
|-------------------------|---------------|
| `Argentina` | `…/team-logos/argentina.png` |
| `South Africa` | `…/team-logos/south-africa.png` |
| `Bosnia & Herzegovina` | `…/team-logos/bosnia-and-herzegovina.png` |
| `USA` | `…/team-logos/usa.png` |

---

## Adding New Approved Logos

1. Obtain the approved, rights-cleared image file
2. Rename to lowercase kebab-case: e.g. `south-korea.png`
3. Place in the correct folder: `team-logos/`, `flags/`, or `badges/`
4. Commit and push to `main`:
   ```bash
   git add team-logos/south-korea.png
   git commit -m "Add South Korea team logo"
   git push
   ```
5. GitHub Pages deploys automatically within ~60 seconds
6. Verify the URL is live:
   ```
   https://sachawd.github.io/wc26-assets/team-logos/south-korea.png
   ```

---

## GitHub Pages Setup

- **Source branch:** `main`
- **Source folder:** `/` (root)
- **Custom domain:** none
- **HTTPS:** enforced by GitHub

Changes pushed to `main` are deployed automatically.

---

## Asset Guidelines

| Property | Requirement |
|----------|-------------|
| Format | PNG preferred (SVG acceptable for flags) |
| Background | Transparent where possible |
| Dimensions | 512×512px minimum for logos |
| Max file size | 500 KB per file |
| Colour space | sRGB |
| Rights | Must be approved/rights-cleared before committing |

---

## Folder Quick Reference

| Folder | Contents | Example filename |
|--------|----------|------------------|
| `team-logos/` | National team badge/crest | `france.png` |
| `flags/` | Country flag images | `france.png` |
| `badges/` | Tournament & event marks | `wc26-official.png` |

---

*Maintained by the Campaign & Design team. Questions? Open an issue on this repo.*
