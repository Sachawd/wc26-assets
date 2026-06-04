# wc26-assets

Public static asset repository for **FIFA World Cup 2026** creative production.

Served via **GitHub Pages** at:

```
https://sachawd.github.io/wc26-assets/
```

**Used by:** Airtable · Table-to-Figma · Figma · Campaign Builder · Kickoff Engine · Social Templates · Email Modules

---

> ⚠️ **SECURITY WARNING**
> This is a **public repository**.
> Never commit API keys, `.env` files, secrets, tokens, or credentials of any kind.
> Only commit approved, rights-cleared static image assets.

---

## Folder Structure

```
wc26-assets/
├── national-team-logos/   # National team badge/crest PNGs
├── club-logos/            # Club crest PNGs (Bundesliga, La Liga, Liga MX, Ligue 1, MLS, Premier League, Serie A)
├── league-logos/          # League identity logos
├── player-headshots/      # Player portrait images (empty — drop files in)
├── flags/                 # Country flag images (empty — drop files in)
├── badges/                # Tournament & event badges (empty — drop files in)
└── README.md
```

---

## Asset Inventory

| Folder | Count | Size |
|--------|-------|------|
| `national-team-logos/` | 70 | ~4 MB |
| `club-logos/` | 160 | ~15 MB |
| `league-logos/` | 8 | ~684 KB |
| `player-headshots/` | 0 | — |
| `flags/` | 0 | — |
| `badges/` | 0 | — |
| **Total** | **238** | **~20 MB** |

---

## Naming Convention

- **Lowercase kebab-case** preferred for new files — no spaces, no uppercase
- Existing filenames are preserved exactly as delivered
- PNG format preferred (transparent background where applicable)

### National Team Logo Examples

| File | URL |
|------|-----|
| `argentina-national-team.png` | `https://sachawd.github.io/wc26-assets/national-team-logos/argentina-national-team.png` |
| `brazil-national-team.png` | `https://sachawd.github.io/wc26-assets/national-team-logos/brazil-national-team.png` |
| `canada-national-team.png` | `https://sachawd.github.io/wc26-assets/national-team-logos/canada-national-team.png` |
| `england-national-team.png` | `https://sachawd.github.io/wc26-assets/national-team-logos/england-national-team.png` |
| `france-national-team.png` | `https://sachawd.github.io/wc26-assets/national-team-logos/france-national-team.png` |
| `germany-national-team.png` | `https://sachawd.github.io/wc26-assets/national-team-logos/germany-national-team.png` |
| `mexico-national-team.png` | `https://sachawd.github.io/wc26-assets/national-team-logos/mexico-national-team.png` |
| `usmnt-national-team.png` | `https://sachawd.github.io/wc26-assets/national-team-logos/usmnt-national-team.png` |

### Club Logo Examples (by league)

| League | File | URL |
|--------|------|-----|
| Premier League | `clubs_arsenal.png` | `…/club-logos/clubs_arsenal.png` |
| La Liga | `club_real-madrid.png` | `…/club-logos/club_real-madrid.png` |
| Bundesliga | `clubs_bayern-munich.png` | `…/club-logos/clubs_bayern-munich.png` |
| MLS | `clubs_la-galaxy.png` | `…/club-logos/clubs_la-galaxy.png` |
| Liga MX | `club_club-america.png` | `…/club-logos/club_club-america.png` |
| Ligue 1 | `clubs_psg.png` | `…/club-logos/clubs_psg.png` |
| Serie A | `clubs_ac-milan.png` | `…/club-logos/clubs_ac-milan.png` |

### League Logo Examples

| File | URL |
|------|-----|
| `league_premier-league.png` | `https://sachawd.github.io/wc26-assets/league-logos/league_premier-league.png` |
| `league_la-liga.png` | `https://sachawd.github.io/wc26-assets/league-logos/league_la-liga.png` |
| `league_bundesliga.png` | `https://sachawd.github.io/wc26-assets/league-logos/league_bundesliga.png` |
| `league_mls.png` | `https://sachawd.github.io/wc26-assets/league-logos/league_mls.png` |
| `league_liga-mx.png` | `https://sachawd.github.io/wc26-assets/league-logos/league_liga-mx.png` |
| `league_ligue-1.png` | `https://sachawd.github.io/wc26-assets/league-logos/league_ligue-1.png` |
| `league_serie-a.png` | `https://sachawd.github.io/wc26-assets/league-logos/league_serie-a.png` |
| `league_nwsl.png` | `https://sachawd.github.io/wc26-assets/league-logos/league_nwsl.png` |

---

## Public Base URL

```
https://sachawd.github.io/wc26-assets/
```

### URL Pattern

```
https://sachawd.github.io/wc26-assets/{folder}/{filename}.png
```

---

## Airtable Formulas

### National Team Logo — from team name field

Use this in a formula field (`Home_Team_Logo_URL`) reading from the `Home_Team` text field:

```
"https://sachawd.github.io/wc26-assets/national-team-logos/"
& LOWER(
    SUBSTITUTE(
      SUBSTITUTE(
        SUBSTITUTE({Home_Team}, " & ", "-and-"),
        " ", "-"
      ),
      "'", ""
    )
  )
& "-national-team.png"
```

**What it produces:**

| `Home_Team` value | Generated URL |
|-------------------|---------------|
| `Argentina` | `…/national-team-logos/argentina-national-team.png` |
| `South Africa` | `…/national-team-logos/south-africa-national-team.png` |
| `South Korea` | `…/national-team-logos/south-korea-national-team.png` |
| `USA` | `…/national-team-logos/usa-national-team.png` *(note: use `usmnt` filename)* |

> **Note on USA:** The file is `usmnt-national-team.png`. If your `Home_Team` field contains `USA`, use an `IF` or `SWITCH` to map it: `IF({Home_Team}="USA","usmnt",LOWER({Home_Team}))`.

### Away Team Logo — same pattern

```
"https://sachawd.github.io/wc26-assets/national-team-logos/"
& LOWER(
    SUBSTITUTE(
      SUBSTITUTE(
        SUBSTITUTE({Away_Team}, " & ", "-and-"),
        " ", "-"
      ),
      "'", ""
    )
  )
& "-national-team.png"
```

### League Logo URL

```
"https://sachawd.github.io/wc26-assets/league-logos/league_"
& LOWER(SUBSTITUTE({League}, " ", "-"))
& ".png"
```

---

## Known Filename Notes

Some existing national team files use **Title Case** (e.g. `Albania-national-team.png`, `Denmark-national-team.png`). These are preserved exactly as received. When referencing them in Airtable formulas, use `LOWER()` to normalise — GitHub Pages URLs **are case-sensitive** on the server side.

**Files with mixed case (use exact URL):**

| Canonical name | Exact filename |
|----------------|----------------|
| Albania | `Albania-national-team.png` |
| Costa Rica | `Costa-Rica-national-team.png` |
| Czech Republic | `Czech-Republic-national-team.png` |
| Denmark | `Denmark-national-team.png` |
| Greece | `Greece-national-team.png` |
| Honduras | `Honduras-national-team.png` |
| Iraq | `Iraq-national-team.png` |
| Ireland | `Ireland-national-team.png` |
| Jamaica | `Jamaican-national-team.png` |
| Nigeria | `Nigeria-national-team.png` |
| Peru | `Peru-national-team.png` |
| Poland | `Poland-national-team.png` |
| Serbia | `Serbia-national-team.png` |
| Slovakia | `Slovakia-national-team.png` |
| Sweden | `Sweden-national-team.png` |
| Trinidad & Tobago | `Trinidad-Tobago-national-team.png` |
| Venezuela | `Venezuela-national-team.png` |

---

## Adding New Approved Assets

1. Confirm the asset is rights-cleared and approved
2. Name the file using **lowercase kebab-case** where possible (e.g. `new-team.png`)
3. Drop into the correct folder: `national-team-logos/`, `club-logos/`, `league-logos/`, etc.
4. Commit and push to `main`:
   ```bash
   git add national-team-logos/new-team.png
   git commit -m "Add [team name] logo"
   git push
   ```
5. GitHub Pages deploys automatically within ~60 seconds
6. Verify the public URL:
   ```
   curl -I https://sachawd.github.io/wc26-assets/national-team-logos/new-team.png
   ```
   Should return `HTTP/2 200`.

---

## GitHub Pages

- **Source branch:** `main` / root
- **Public URL:** `https://sachawd.github.io/wc26-assets/`
- **HTTPS:** enforced
- **Deploy time:** ~60 seconds after push

---

## Asset Guidelines for New Files

| Property | Requirement |
|----------|-------------|
| Format | PNG (transparent bg preferred) |
| Min dimensions | 512×512px for logos |
| Max file size | 500 KB per file |
| Colour space | sRGB |
| Naming | lowercase-kebab-case.png |
| Rights | Must be approved before committing |

---

*Maintained by the Campaign & Design team.*
