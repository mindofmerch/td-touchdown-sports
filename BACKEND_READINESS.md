# Backend readiness and verified gaps

Verified 2026-10-28 UTC. This record carries forward the prior Y.E.S. Arena / Touchdown Vortex decisions into this repository.

## Current repository and live route

- This private repository is a continuity and deployment bridge. It currently contains routing configuration and project records; it does not contain the original arena UI source.
- The established public arena remains at https://yes-td-vortex.jessicasalasr209.chatgpt.site. Preserve its approved UI: MATCHUP, 11V11 FIELD, VEGAS INSIDER, WHAT-IF ISLAND, PARLAY LAB, FULL SLATE, and MIX IT UP.
- The Vercel rewrite routes /api/bootstrap to Supabase function yes-sports-app-holo, /api/brain to yes-history-echo-public, and other paths to the existing arena site. Production was not changed in this audit.
- Vercel project yes-sports-anomaly-lab is healthy, but is not linked to this private repository. Vercel's GitHub integration returned repo_not_found for mindofmerch/td-touchdown-sports; the repository is not yet granted to that installation.

## Historical store inventory

The source-of-truth records remain in the existing Supabase project. These are counts only; no historical rows were copied or rewritten.

| Table | Rows |
|---|---:|
| nfl_historical_games | 7,383 |
| nfl_team_pregame_features | 17,644 |
| nfl_game_personnel_snapshots | 14,766 |
| yes_td_outcomes | 7,447 |
| yes_historical_analogs | 2,378 |
| yes_brain_runs | 6,011 |
| yes_postgame_reviews | 107 |
| private.nfl_market_snapshots | 303,484 |
| canonical_private.temporal_game_memory_v1 | 51,910 |
| canonical_private.research_state_snapshots_v1 | 2,382 |
| canonical_private.research_signals_v1 | 10,011 |
| canonical_private.game_research_state_v1 | 89 |
| yes_prediction_locks_v2 / yes_prediction_grades_v2 | 1 / 1 |
| yes_td_publications / yes_td_research_snapshots | 8 / 0 |

## Verified personnel readiness gap

- yes_personnel_analogs_v2 delegates to canonical_private.search_personnel_analogs_v2.
- That search uses canonical_private.game_personnel_features_v1, filters historical examples to coverage of at least 80, and requires completed games. It does not search nfl_game_personnel_snapshots directly.
- The canonical personnel feature table has 8,752 rows overall and 62 rows for 2026. The raw snapshot table has 214 rows for 2026.
- No canonical personnel feature or raw personnel snapshot exists for 2026_W08_CAR_GB, and the canonical table has no CAR–GB row for season 2026, week 8. Therefore this target cannot qualify for personnel analogs from the current build path.
- The live One Brain response for CAR–GB, 2026 week 8, returned BLOCKED and final_prediction_authorized: false, with source-data and personnel-history blockers. Keep this gate in place until verified inputs and a valid build are available.

## Model evidence and rating

The live endpoint reported 855 combined holdout games, 8D MAE 10.79, and winner accuracy 61.99%. Year holdouts: 2023 (285 games, 61.54%, MAE 10.906), 2024 (64.21%, MAE 10.724), and 2025 (60.35%, MAE 10.738). These are measured history, not a guarantee of future accuracy. No shared factor rubric defines what 9+ means, so no overall score is asserted.

## Security and change status

- Supabase Security Advisor flagged RLS disabled on 16 tables: private.yes_backtest_game_features_v1, private.yes_player_weekly_history, private.yes_model_lessons; and yes_private.v10_game_states, v10_mirror_edges, v10_motifs, v10_model_registry, v10_prediction_locks, v10_candidate_edges, v10_head_models, v10_expert_predictions, v10_crossbreed_models, v10_crossbreed_heldout, v10_hazard_thresholds, v10_hazard_models, v10_branch_models.
- No RLS or policy changes were applied. Policies must be mapped to actual service and client access before enabling RLS, or legitimate backend reads could break.
- No secrets, raw personal data, or full historical records are stored in this repository.

## Next work

1. Grant the Vercel GitHub App installation access to this private repository, then link it to the intended Vercel project and verify the production/preview deployment path.
2. Recover the original arena source through the approved Sites source workflow and mirror it here without changing its UI.
3. Trace the current schedule, verified injury report, and depth-chart feed into the personnel feature builder. Do not infer absent target data from historical rows.
4. Design and review least-privilege RLS policies for the 16 flagged tables before applying any RLS changes.
5. Define a factor-by-factor acceptance rubric and report scores only after repeatable end-to-end evidence exists.
