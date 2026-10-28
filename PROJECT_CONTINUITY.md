# TD Touchdown Sports — project continuity

Reconciled against GitHub, Vercel, Sites, and Supabase on 2026-10-28 05:01 UTC. This record contains no database rows, API keys, or sync credentials.

## Current deployment map

- GitHub bridge repo: https://github.com/mindofmerch/td-touchdown-sports (public, main).
- Vercel project: td-touchdown-sports, linked to this repo and main. Latest production deployment 0ad27fd3aed92a17180e5777d2cd7227e45585c8 is READY.
- Public app: https://td-touchdown-sports.vercel.app/. Root serves the approved arena. /api/brain?action=health returns HTTP 200 and database=connected.
- Published arena: https://yes-td-vortex.jessicasalasr209.chatgpt.site/. Its approved interface is preserved. The source is not yet checked into this GitHub repository; the current deployment is a bridge to the published Site.
- Supabase project: cnqyxhazmctvboxaosut (us-east-2). The older yes-sports-anomaly-lab project remains separate and was not replaced.
- vercel.json routes /api/bootstrap to yes-sports-app-holo, /api/brain to yes-history-echo-public, and root/wildcard paths to the arena. Baseline no-store/security headers remain set.

## Locked product decisions

- Keep the holographic arena, Vortex, and navigation design. Work on backend, data quality, and delivery without redesigning.
- Preserve MATCHUP, 11V11 FIELD, VEGAS INSIDER, WHAT-IF ISLAND, PARLAY LAB, FULL SLATE, and MIX IT UP. Parlay sets support 3/5/7/10 legs with unique games per ticket.
- Bind game identity to season, week, away, home, and request generation. All views use one canonical One Brain response; reject stale responses after matchup changes.
- Keep measured TD counts, red-zone/inside-five usage, opportunity versus scoring trajectories, injury/personnel evidence, Gold Script, and pre-kickoff history distinct.
- Never fabricate probabilities, quarter scores, similarity rates, prices, or advantage. Show source and retrieval times separately. Final predictions remain gated on verified inputs.

## Live verification — 2026 Week 8 CAR at GB

- Production health route: HTTP 200; database connected; build matchup-model-20261017.
- Production matchup API: HTTP 200 and canonical One Brain response, but readiness is BLOCKED; final_prediction_authorized=false.
- Blockers: SOURCE_DATA_NOT_READY, PERSONNEL_HISTORY_NOT_READY, PERSONNEL_MODEL_NOT_APPLIED. Injury evidence is connected but unapplied; final inactives and key starting groups remain unverified.
- Structural holdout: 855 games, 8D MAE 10.79, winner accuracy 61.99%. These historical results are not a guarantee or a 9+ overall rating.
- No common factor-rating rubric is defined yet. Do not claim a score until measurable criteria and repeatable evidence exist.

## Historical store and remaining work

Earlier read-only Supabase counts: 7,383 games; 17,644 team pregame features; 14,766 personnel snapshots; 7,447 TD outcomes; 2,378 analogs; 6,011 One Brain runs; 107 postgame reviews; 303,484 market snapshots; 51,910 temporal-memory rows; 2,382 research snapshots; 10,011 research signals; 89 game research states; 1 prediction lock / 1 grade; 8 TD publications / 0 TD research snapshots. Supabase remains the historical source of truth; these rows were not copied into GitHub.

- Historical schedule/stats: nflverse protected feeds. Current roster identity: ESPN team roster. Weather: Open-Meteo. Target market status was reference-fresh; publishable quote provenance remains unverified.
- Protected syncs require server-side one-time credentials. Never guess or commit them.
- Security Advisor previously flagged RLS disabled on 16 tables in private and yes_private. Review per-table access before making policy changes; no RLS changes were applied.
- Next: recover and version the approved arena source without visual changes; close source/personnel gates through authorized data paths; connect TD research to the canonical response; review RLS; then verify regression, mobile/accessibility, source freshness, and deployment end-to-end.

## Historical references

- Week 1 reference Site: https://nfl-week-one-command-center.jessicasalasr209.chatgpt.site/ (not production).
- Historical Vercel command centers: https://nfl-level-15-2-command-center.vercel.app/ and https://nfl-level-11-command-center-merchs-projects-c5bf540e.vercel.app/ (not re-verified).
- ESPN FPI, FTN/DVOA, Action Network, SportsLine, CBS simulations, and sportsbook consensus are comparison targets until current sources and rights are verified.
