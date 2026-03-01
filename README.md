# GoogleSheetsRoster

A single-page roster dashboard that pulls live data from a publicly published Google Sheet. Open `index.html` in any browser — no build step or server required.

## Configuration

All settings live in `config.json`:

```json
{
  "sheetTsvUrl": "https://...",
  "leagueName": "My League",
  "theme": {
    "pageBg": "#0f172a",
    "surfaceBg": "#1e293b",
    "accent": "#60a5fa",
    "border": "#334155",
    "textPrimary": "#ffffff"
  }
}
```

### Settings

| Key | Description |
|-----|-------------|
| `sheetTsvUrl` | The published-as-TSV URL from Google Sheets (see below) |
| `leagueName` | Displayed as the page title and main heading |

### Theme

| Key | Applies to |
|-----|-----------|
| `pageBg` | Page background and table header row background |
| `surfaceBg` | Table row cells, search input, mobile cards |
| `accent` | Table header text, search focus ring, status badge, heading underline, active pagination button |
| `border` | Table cell borders, input borders, footer divider, row hover highlight |
| `textPrimary` | All primary text (player names, search input). Muted text (team names, pagination summary, timestamp) is derived automatically as a dimmed version of this color. |

## Google Sheet Setup

1. Create a sheet with columns: `Player`, `Pos`, `Org`, `Team`
2. In Google Sheets go to **File → Share → Publish to web**
3. Choose the correct sheet tab, select **Tab-separated values (.tsv)**, and click **Publish**
4. Copy the URL and set it as `sheetTsvUrl` in `config.json`

### Column values

- **Pos** — slash- or comma-separated position codes, e.g. `SP/RP` or `1B,OF`
- **Org** — MLB team abbreviation, e.g. `LAD`. Use `---` for no org.
- Rows where Player is `Empty` and Pos/Org are blank are hidden by default
