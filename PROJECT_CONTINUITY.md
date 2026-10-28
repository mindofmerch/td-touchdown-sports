# TD Touchdown Sports — project continuity

Reconciled against the connected GitHub, Vercel, Sites, and Supabase sources on 2026-10-28 UTC. This file records architecture and status; it does not contain database rows, API keys, or sync credentials.

## Current deployment map

- GitHub source repo: `https://github.com/mindofmerch/td-touchdown-sports` (private).
- Vercel production app: `https://yes-sports-anomaly-lab.vercel.app/` (project `yes-sports-anomaly-lab`).
- Published arena Site: `https://yes-td-vortex.jessicasalasr209.chatgpt.site/` (Y.E.S. Arena, version 46; this is the source of the established interface).
- Supabase project: `cnqyxhazmctvboxaosut` (`us-east-2`).
- `vercel.json` in this repository routes `/api/bootstrap` to the `yes-sports-app-holo` Edge Function, `/api/brain` to `yes-history-echo-public`, and other paths to the published arena Site. It also carries forward no-store and baseline response security headers.
- The current Vercel production project remains separate from this new repo. Do not replace or redirect it without validating a new source deployment.

## Historical product decisions

- Keep the established holographic arena, Vortex, and navigation design locked. Continue backend and data-quality work without redesigning the interface.
- Preserve the approved MATCHUP, 11V11 FIELD, VEGAS INSIDER, WHAT-IF ISLAND, PARLAY LAB, FULL SLATE, and MIX IT UP surfaces. Parlay sets support 3/5/7/10 legs with unique games per ticket.
- Keep game identity bound across season, week, away team, home team, and request generation. All tabs must use one canonical One Brain response; reject stale responses after matchup changes.
- Preserve measured touchdown counts, red-zone/inside-five usage, opportunity versus scoring trajectories, injury and personnel evidence, Gold Script, and pre-kickoff prediction history as separate evidence.
- Never fabricate probabilities, quarter scores, similarity rates, market prices, or predictive advantage. Show source time separately from retrieval time and keep final predictions gated on verified data.

## Verified backend snapshot

Supabase SQL read-only counts during this reconciliation:

- Historical NFL games: 7,383.
- Team pregame feature rows: 17,644.
- Game personnel snapshots: 14,766.
- Touchdown outcome rows: 7,447.
- Historical analog rows: 2,378.
- One Brain runs: 6,011.
- Postgame reviews: 107.
- Market snapshots: 303,484.
- Temporal game-memory rows: 51,910.
- Research snapshots/signals/game research states: 2,382 / 10,011 / 89.
- Prediction locks and grades: 1 / 1.
- TD-specific research snapshots: 0.

The live matchup response for 2026 Week 8, CAR at GB, was `ok` but `BLOCKED`: final prediction authorization was false because verified game input status and historical personnel readiness were missing, and the personnel scenario model was not applied. Keep this block until the inputs are verified; do not bypass it to produce a score.

The stored walk-forward structural holdout covered 855 games. Its 8-dimension track reported 10.79 points MAE and 61.99% winner accuracy; the rolling 2023–2025 holdouts ranged from 60.35% to 64.21% winner accuracy. These are evaluation records, not a 9+ overall quality rating. No composite factor-rating rubric was found.

## Verified source feeds and gaps

- Historical schedule, player/team weekly stats: nflverse release data, accessed by existing protected sync functions.
- Current roster identity: ESPN team roster feed.
- Weather evidence: Open-Meteo; CAR–GB response marked weather neutral.
- Market response: reference-fresh status, but a publishable odds source and quote provenance still need to be verified.
- The sync functions require a server-side `x-yes-sync-key`; never store or copy that value into this repository or a browser client.
- Supabase Security Advisor currently flags 16 tables across `private` and `yes_private` as having RLS disabled. Review per-table access policies before changing RLS; do not enable it blindly.

## Historical sites and references

- Current arena: `https://yes-td-vortex.jessicasalasr209.chatgpt.site/`.
- Historical Week 1 command center Site: `https://nfl-week-one-command-center.jessicasalasr209.chatgpt.site/` (reference only; do not treat it as production).
- Earlier Vercel command-center links saved from prior work: `https://nfl-level-15-2-command-center.vercel.app/` and `https://nfl-level-11-command-center-merchs-projects-c5bf540e.vercel.app/` (historical references; current status not re-verified).
- Model-comparison sources previously discussed: ESPN FPI, FTN/DVOA, Action Network, SportsLine, CBS simulations, and sportsbook consensus. Treat these as comparison targets until a current feed and data rights are verified.

## Next work order

1. Resolve verified current-game inputs, personnel history, injury/depth snapshots, and source freshness before widening prediction authorization.
2. Improve out-of-sample calibration and retain immutable prediction locks and grades. Report sample size and uncertainty.
3. Connect TD opportunity research snapshots, saved research, and parlay candidates to the same canonical matchup response.
4. Review RLS and policies for the 16 flagged tables before exposing any table through the Data API.
5. Connect this GitHub repo to Vercel only after the account grants the Vercel GitHub integration access to this private repository.

The Supabase database remains the historical data store; this document records its measured state and routing, not a copy of its records.
