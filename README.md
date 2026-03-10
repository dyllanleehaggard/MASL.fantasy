# MASL Fantasy — Indoor Elite

A dark-themed MASL fantasy soccer app built as a single HTML file. No frameworks, no build step — just drop it on GitHub Pages and go.

---

## Features

- **User Accounts** — Register/login with localStorage-based auth (no backend required)
- **Draft Your Squad** — Pick 1 GK, 2 DEF, 2 MID, 1 FWD within a $100M budget
- **Locked Roster** — Once you confirm your squad, it's locked for the season
- **Free Transfers** — 5 per season; use them to swap players after lock-in
- **Player Leveling** — Players earn XP from points scored; 5 levels with score multipliers
- **Leaderboard** — See all managers ranked by total points
- **Scoring Guide** — Full breakdown of how points are earned per position
- **Dark Theme** — Bold Barlow Condensed typography, teal/orange accent palette

---

## Deploy to GitHub Pages

1. Create a new GitHub repository
2. Upload `index.html` to the root
3. Go to **Settings → Pages → Deploy from branch → main / root**
4. Your app will be live at `https://yourusername.github.io/repo-name`

---

## Updating Player Data

All player data lives in the `PLAYERS` array inside `index.html` (around line 250 in the `<script>` block). Each player object looks like:

```js
{ id: 21, name: 'Pável Pérez', pos: 'FWD', team: 'San Diego Sockers', cost: 18, pts: 130, xp: 130 }
```

**Fields:**
- `id` — Unique integer, do not duplicate
- `name` — Player display name
- `pos` — `GK`, `DEF`, `MID`, or `FWD`
- `team` — MASL team name
- `cost` — Cost in $M (budget is $100M per squad)
- `pts` — Current season points total
- `xp` — XP = same as pts; drives leveling

To update scores after a game week, find the player by name and update `pts` and `xp`.

---

## Leveling System

| Level | XP Range | Multiplier | Label   |
|-------|----------|------------|---------|
| 1     | 0–50     | ×1.0       | Rookie  |
| 2     | 51–150   | ×1.1       | Pro     |
| 3     | 151–300  | ×1.25      | Elite   |
| 4     | 301–500  | ×1.4       | Star    |
| 5     | 501+     | ×1.6       | Legend  |

---

## Scoring Rules (Summary)

| Action                     | Points     |
|----------------------------|------------|
| Goal (outfield)            | +10        |
| Assist                     | +6–7       |
| Team Win                   | +4         |
| Clean Sheet (GK)           | +8         |
| Clean Sheet (DEF)          | +6         |
| Save                       | +1         |
| 5+ Saves (bonus)           | +3         |
| MOTM                       | +5         |
| Hat Trick Bonus (FWD)      | +8         |
| Yellow Card                | -1         |
| Red Card                   | -3         |

---

## Roadmap (Future)

- [ ] Admin panel to update scores without editing HTML
- [ ] Weekly gameweek history
- [ ] Player form/trending indicators
- [ ] Supabase backend for real persistence across devices
- [ ] Automatic MASL stats import

---

Built with ♟ by Footy Collective
