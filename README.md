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
- Add complete individual games in `data/matches.json`. Use the player IDs `mt` and `bean`; each match stores its crown score, winner, source image, and both eight-card decks.
- Assign match IDs to rounds in `data/series.json`. Round one is first to 8 game wins; rounds two through seven are first to 9; a series ends at 4 round wins.
- The seven clipped screenshot entries are in `unresolvedEntries` in `data/matches.json`. The site excludes them from statistics until their scores and decks can be read.

The imported screenshot set contains 15 fully visible games. Their captured round placement is provisional because the screenshots do not show round boundaries. Dates are not present in the images and are left blank.
