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
- Assign match IDs to rounds in `data/series.json`. Round one is first to 8 game wins; round two is first to 9; rounds three, four and five are first to 10; rounds six and seven are first to 9; a series ends at 4 round wins. The per-round targets are in `format.roundGameTargets`, and each round's own `gameTarget` field in `data/series.json` is what the site actually uses. Round and series standings are calculated from those match IDs.
- The clipped screenshot entries are in `unresolvedEntries` in `data/matches.json` (shown at the bottom of the Matches page). The site excludes them from statistics until their scores and decks can be read.
- Games that are in `data/matches.json` but not in any round's `matchIds` are treated as **unassigned**: they count in overall statistics (home, players, records, cards, analytics) and appear on the Rounds and Series pages under "Games not yet in a round", but not in any round or series result. To assign them, add their IDs to a round in `data/series.json` (or add a new round).
- `gameNumber` can skip values on purpose (Round 2 begins at roundGame 6 because its first five games were never captured), so the Round log and game pages show `roundGame` and the overall `gameNumber`.
- Games are numbered oldest to newest (`gameNumber`, `roundGame`). In each screenshot the lower game is the older one. Each game also stores `trophies`, `cardLevels` (every card shown was Lvl.11) and `replayAvailable`; players have `clan` and `country` in `data/players.json`.

The archive contains 72 fully visible games: Round 1 (m01–m15), Round 2 (m16–m31), Round 3 (m32–m42, TheBeanWithDrip won 10–1), Round 4 (m43–m53, TheBeanWithDrip won 10–1; m50 and m51 come from R4_Game8and9.PNG and m52 and m53 from R4_Game10and11.PNG) and Round 5 (m54–m64 from R5_Game1and2.PNG through R5_Game11.PNG, TheBeanWithDrip won 10–1; m64 has no age label and shows later trophies, MT 9185 and Bean 7011, so its placement is provisional). With Round 5 complete, TheBeanWithDrip has four round wins. m65 to m72 (Later_Game1and2.PNG through Later_Game7and8.PNG, 17h 25min to 16h 46min before those screenshots, same trophies as m64, replays no longer available) are not yet assigned to a round or series. Six clipped screenshot entries (u01, u02, u04, u06, u08, u17) are excluded from statistics. Below is the original note on the first screenshot sets:

The first 20 games come from the screenshots Game1and2.PNG through Game15.PNG (Round 1, 15 games) and Game1.PNG, Game2and3.PNG and Game4and5.PNG (Round 2, 5 games). Round 1 ends at Game 15, where MT reaches 8 wins (8–7). The visible 1d 13h / 1d 14h Battle Log ages place the Round 1 games on October 18, 2026, and the Round 2 screenshots establish October 20, 2026. Card names are visual identifications from the card artwork.

## Pages

- `index.html` — series banner (shows "Series complete" once a player has 4 round wins), round track, game record, recent games, form chart and data-completeness status.
- `records.html` — milestones, personal bests, streaks and a round leaderboard, with links to each game page.
- `game.html?id=m16` — individual crown score, trophies, both decks, round tally, source, and previous/next navigation across all games in order. Replace `m16` with another match ID.
- `rounds.html` — round scoreboards, crown totals and averages, close games, shutouts, streaks, standout scores, card usage, repeated deck pairs, linked game logs, and the unassigned-games panel.
- `matches.html` — every game, newest first by default, with search, round (including Unassigned), winner, score and sort filters and a live result count.
- `series.html`, `players.html`, `cards.html`, and `analytics.html` — series and round breakdowns, player and card statistics, and score analytics.
