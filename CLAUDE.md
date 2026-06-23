# Biotech Intelligence Desk

## Agent Team

- pdufa-analyst
- watchlist-architect
- analyst-ratings
- hedge-fund-analyst
- biotech-cio

## Project Purpose

This repository supports a multi-agent biotechnology investment research workflow.

The system should:

- Track PDUFA dates and FDA regulatory catalysts
- Maintain biotech watchlists
- Monitor analyst ratings and market expectations
- Produce institutional-style biotech investment research
- Document conflicts, uncertainties, and material changes

## Core Rules

1. Accuracy is more important than speed.
2. Prefer primary sources.
3. Include source links and publication dates for material claims.
4. Clearly distinguish verified facts, company claims, analyst estimates, calculations, inferences, and unknown information.
5. Never invent PDUFA dates, analyst commentary, clinical results, financial figures, or price targets.
6. Mark regulatory dates as confirmed, estimated, changed, delayed, or unverified.
7. Do not treat analyst ratings as proof that a stock should be purchased.
8. Do not treat company presentations as independent evidence.
9. Document meaningful changes rather than silently replacing old information.
10. No agent may execute trades.
11. No agent may claim certainty about clinical, regulatory, or stock-price outcomes.
12. Human review is required before investment decisions.

## Source Priority

Use sources in this order whenever available:

1. FDA and other government sources
2. SEC filings
3. ClinicalTrials.gov
4. Peer-reviewed scientific and medical publications
5. Scientific conference presentations
6. Company investor-relations disclosures
7. Earnings-call transcripts
8. Established financial news sources
9. Reputable financial databases
10. Social media only as a research lead

## File Locations

- Structured data belongs in `data/`
- Reports belong in `reports/`
- Company investment memos belong in `research/`
- Conflicts and unresolved issues belong in `logs/conflicts.md`
- Agent definitions belong in `.claude/agents/`

## Standard Workflow

Run the research process in this order:

1. `pdufa-analyst`
2. `watchlist-architect`
3. `analyst-ratings`
4. `hedge-fund-analyst`

Each agent should read relevant existing files before updating its own outputs.

## PDUFA Analyst Workflow

The `pdufa-analyst` should:

1. Research current FDA and regulatory catalysts.
2. Update `data/pdufa_calendar.csv`.
3. Update `reports/pdufa_weekly.md`.
4. Record unresolved discrepancies in `logs/conflicts.md`.
5. Never invent exact regulatory dates.

## Watchlist Architect Workflow

The `watchlist-architect` should:

1. Read `data/pdufa_calendar.csv`.
2. Update `data/biotech_watchlist.csv`.
3. Update `reports/watchlist_changes.md`.
4. Document additions, removals, and score changes.
5. Flag cash-runway and dilution risks.

## Analyst Ratings Workflow

The `analyst-ratings` agent should:

1. Read `data/biotech_watchlist.csv`.
2. Read `data/pdufa_calendar.csv`.
3. Update `data/analyst_actions.csv`.
4. Update `reports/analyst_consensus.md`.
5. Flag stale ratings and inaccessible paywalled commentary.
6. Treat analyst consensus as market-expectations data, not independent evidence.

## Hedge Fund Analyst Workflow

The `hedge-fund-analyst` should:

1. Read the watchlist, PDUFA calendar, analyst actions, and analyst consensus report.
2. Review scientific, clinical, regulatory, commercial, financial, and valuation evidence.
3. Create company memos in `research/`.
4. Update `data/company_scores.json`.
5. Record unresolved discrepancies in `logs/conflicts.md`.
6. Preserve prior conclusions and document thesis changes.
7. Never use analyst ratings as the primary investment thesis.
## Biotech CIO Workflow

The `biotech-cio` should:

1. Run only after the other four agents have completed their current research cycle.
2. Read all current files in `data/`, `reports/`, `research/`, and `logs/`.
3. Audit PDUFA dates, watchlist classifications, analyst actions, company scores, and investment memos.
4. Identify stale, incomplete, conflicting, or unsupported information.
5. Review `logs/conflicts.md` before producing a final report.
6. Assign company-priority statuses.
7. Produce `reports/daily_biotech_brief.md`.
8. Produce `reports/weekly_cio_report.md`.
9. Preserve unresolved conflicts and carry them into future reports.
10. Never execute trades or convert uncertain research into a guaranteed prediction.

## Full Team Workflow

Run the team in this order:

1. `pdufa-analyst`
2. `watchlist-architect`
3. `analyst-ratings`
4. `hedge-fund-analyst`
5. `biotech-cio`

The `biotech-cio` is the final review and quality-control agent.
