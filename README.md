# ransom-radar

A browser-based feed for tracking ransomware data leak site victims in near real-time.
Data is pulled from [ransomware.live](https://www.ransomware.live) via their public API.
No backend, no install — open `index.html` in a browser.

---

## What it shows

- A live scrollable table of recent victims with date, target, sector, threat actor, and country
- A stats ribbon showing today's count, yesterday's delta, 7-day totals, top group, top sector, and a trend sparkline
- A sidebar with ranked groups and sectors, each clickable to filter the feed
- A scrolling ticker at the bottom summarising the full dataset
- An expandable detail panel per row showing description, domain, screenshot, ransom amount, infostealer stats, and a link to the ransomware.live entry

## Filtering

The filter bar at the top accepts a free-text search (matches victim name and domain) and dropdown filters for group, sector, and country. Clicking a sector tag inside the feed or any row in the sidebar also applies a filter. All stats update to reflect the active filter. CLR resets everything.

## Running it

Open `index.html` with a local server. The API requires CORS headers that browsers block on `file://` protocol.

The quickest options:

```
# VS Code Live Server extension — right-click index.html, Open with Live Server
# Python
python -m http.server 8000
# Node
npx serve .
```

The app tries the ransomware.live API directly first, then falls back to two public CORS proxies (corsproxy.io and allorigins.win) if the direct request is blocked.

## Data source

All data comes from the [ransomware.live](https://www.ransomware.live) public REST API. No API key is required. The feed auto-refreshes every 5 minutes.

## Notes

- Tested in Chrome and Edge on Windows
- Flag emojis are not used — country codes are displayed as text for cross-platform consistency
- No frameworks, no build step, no dependencies beyond a Google Fonts import
