# Drive to Survive — Fantasy Basketball Tracker

## What this project is
A single-file static web app for tracking a 23-person NBA playoff fantasy league called "Drive to Survive". The entire app lives in `index.html` — do not split into separate JS/CSS files. It is hosted on GitHub Pages.

## League Rules
- 23 fantasy teams (see team list below)
- Each team picks one NBA player per night there are games
- Each player can only be used once per team for the entire season
- Scoring: every point, rebound, assist, block, steal = 1 pt. Turnovers = -1 pt
- **Lone Wolf Prize**: highest score by any team on a night where they were the ONLY team to pick that player. Season-long best single score wins. Ties split the prize.

## Fantasy Teams (in standings order as of Apr 29)
HenryJ, Koonal, Zinger in ya Stinker, Alex0911, Jfok, Titanic, Deevy, Hotchuckolate, It's Klebering Time, Dopeboymagic23, Diddy Got Giddey, Shawnuberoi, Paladizzle, NickelNdime, GokulAgrawal, LakersFan22, GoTheDistance, Lmcclelland, GayforJs, WolvesInThisBih, Jimbo17, Rramchandani, Mdbrenyo

## How to update picks nightly

### Option A — Screenshot provided
The user will paste or describe a screenshot of fantasypostseason.com showing the standings/log with each team's starter and daily points. Extract:
- Date (use YYYY-MM-DD format)
- Team name (match exactly to the list above)
- Player name (full name preferred, e.g. "Cade Cunningham" not "C. Cunningham")
- Score (the daily pts number, as a float)

Then update `index.html` by finding the `const SEED_PICKS = [...]` array and appending the new picks. Remove any existing picks for the same date first to avoid duplicates.

### Option B — Manual data provided
User will tell you picks in plain text. Parse it and do the same update.

### After updating picks
1. Update the seed picks array in `index.html`
2. Commit with a message like `"Add picks for YYYY-MM-DD"`
3. Push to main branch
4. GitHub Pages will auto-deploy within ~2 minutes

## File structure
```
01_drive_to_survive/
  index.html        ← entire app, never split this up
  CLAUDE.md         ← this file
  .git/
```

## Key data structure
Picks are stored as a JSON array inside `index.html`:
```js
const SEED_PICKS = [
  {"date": "2026-04-18", "team": "HenryJ", "player": "Joel Embiid", "score": 43.0},
  ...
];
```

The app merges SEED_PICKS with any picks stored in the user's localStorage (for picks added via the in-app Entry tab). SEED_PICKS always wins for dates it covers.

## Vehicle sprites
Each team can have a custom 8x16 pixel art vehicle sprite stored in `customSprites` in localStorage. These are generated via the Vehicle Workshop in the Entry tab. Do not touch these unless asked.

## GitHub setup
- Repo: check `git remote -v` for the current remote URL
- Branch: main
- GitHub Pages: enabled, serving from root of main branch
- To push: `git add index.html && git commit -m "message" && git push origin main`

## Things NOT to do
- Do not split `index.html` into multiple files
- Do not add a build step or bundler
- Do not add external dependencies beyond the Google Fonts already loaded
- Do not change the scoring logic without being asked
- Do not modify the TEAMS array order (it maps to TEAM_COLORS)

## Current season status
- Playoffs: 2025 NBA Playoffs
- Data loaded through: April 29, 2026
- Active NBA teams: BOS, NYK, MIL, IND, CLE, ORL, MIA, ATL, OKC, LAL, GSW, MEM, DEN, LAC, PHX, SAC
- Eliminated: PHI, DET, POR, SAS
