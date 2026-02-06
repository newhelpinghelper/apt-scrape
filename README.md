> Lightweight, fault-tolerant scraper for tracking apartment pricing over time.

# Apartment Floorplan Price Scraper

This project scrapes unit-level pricing and availability data from an apartment building’s public floorplans page and appends daily snapshots to a CSV for longitudinal analysis.

The scraper is designed to:
- run unattended (via `launchd` or cron),
- avoid duplicate daily runs,
- fail safely on network or site issues,
- keep all private / location-specific information out of version control.

---

## What this does

On each run, the scraper:
1. Fetches the main floorplans page
2. Discovers individual floorplan URLs
3. Extracts unit ID, price, availability, and metadata
4. Appends results to a CSV (one row per unit per day)

This enables tracking:
- price changes over time
- availability dynamics
- unit-level churn

---

## Project structure

```
apt_scrape/
├── apt_scrapes.ipynb              # Main scraper notebook
├── run_apt_scrapes.sh.example     # Example runner script (safe to commit)
├── config.example.json            # Example config (no private data)
├── .gitignore
├── runs/                          # Daily executed notebooks (ignored)
└── run_state/                     # Lock + marker files (ignored)
```
