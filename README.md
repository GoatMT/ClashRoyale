# Arena Ledger

A static Clash Royale rivalry archive built with HTML, CSS, JavaScript, and JSON. It runs without a backend; the browser loads the files in `data/` directly.

## Run locally

From this folder, start a static file server:

```powershell
python -m http.server 8000
```

Then open <http://localhost:8000>. If Python is not installed, use the **Live Server** extension in Visual Studio Code and open `index.html` with it. Opening the HTML file directly (`file://`) will not load the JSON data because browsers restrict local file requests.

## Publish with GitHub Pages

1. Push this folder to a GitHub repository.
2. In the repository, open **Settings → Pages**.
3. Select **Deploy from a branch**, choose the branch containing the site and the `/ (root)` folder, then save.
4. Open the Pages URL shown in the settings panel.

All paths are relative, so the site works at a GitHub Pages project URL as well as the root URL.

## Update the archive

- Add or edit player profiles in `data/players.json`.
- Add complete individual games in `data/matches.json`. Use the player IDs `mt` and `bean`; each match stores its crown score, winner, source image, and both eight-card decks. Match cards link to a dedicated game record at `game.html?id=mNN`.
- Maintain card type and overlapping gameplay-role labels in `data/card-types.json`. The Card Statistics page and every displayed deck read from this shared catalog. Add new non-troop types and role tags there when the archive grows; uncategorized cards display as Troop / Support.
- Assign match IDs to rounds in `data/series.json`. Round one is first to 8 game wins; rounds two through seven are first to 9; a series ends at 4 round wins. Round and series standings are calculated from those match IDs.
- The ten clipped or potentially duplicated screenshot entries are in `unresolvedEntries` in `data/matches.json`. The site excludes them from statistics until their scores and decks can be read.

The archive contains 20 fully visible games from IMG_3270.PNG through IMG_3280.PNG. The first 15 are provisionally grouped into Round 1; the five complete games in IMG_3278.PNG through IMG_3280.PNG are recorded as Round 2 per the user's note. The screenshots do not show the original beginning/end of round boundaries, so Round 1 placement remains provisional. Screenshot capture metadata places the Round 1 log on October 20, 2026; the visible 1d 13h / 1d 14h Battle Log ages place those games on October 18, 2026. The screenshots do not establish exact match times, so only the calendar date is recorded. Round 2 screenshots establish October 20, 2026 as the game date. Card names are visual identifications from the card artwork.

## Pages

- `index.html` — current best-of-7 dashboard and Round 2 progress.
- `records.html` — searchable, filterable record index, with dedicated game-page links and flagged partial captures.
- `game.html?id=m16` — individual crown score, player-versus-player result, round tally, both decks, source, and neighboring game navigation. Replace `m16` with another match ID.
- `rounds.html` — round scoreboards, crown totals and averages, close games, shutouts, streaks, standout scores, card usage, repeated deck pairs, and linked game logs.
- `matches.html`, `series.html`, `players.html`, `cards.html`, and `analytics.html` — history, round breakdowns, player/card statistics, and analytics.
