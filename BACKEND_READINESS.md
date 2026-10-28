# Backend readiness and verified gaps

Verified 2026-10-28 05:01 UTC. The historical data remains in Supabase; this repository contains no raw game records, personal data, or credentials.

## GitHub → Vercel → Supabase bridge

- GitHub repo: https://github.com/mindofmerch/td-touchdown-sports (public, main).
- Vercel project: td-touchdown-sports, connected to this repository and main. Production deployment 0ad27fd3aed92a17180e5777d2cd7227e45585c8 is READY.
- Public app: https://td-touchdown-sports.vercel.app/. Root serves the approved arena. /api/brain?action=health returns HTTP 200, ok=true, database=connected.
- The repo is still a bridge, not the original arena source. Root and wildcard paths rewrite to https://yes-td-vortex.jessicasalasr209.chatgpt.site; API paths route to existing Supabase functions. The approved UI was not redesigned.
- This closes the repository access, deployment link, root route, and health-route bridge checks. It does not close source recovery or matchup data readiness.

## Live matchup readiness: 2026 Week 8 CAR at GB

A fresh production API request returned HTTP 200 and a canonical One Brain response, but remains BLOCKED with final_prediction_authorized=false. Keep the gate in place.

- Blocking reasons: SOURCE_DATA_NOT_READY, PERSONNEL_HISTORY_NOT_READY, PERSONNEL_MODEL_NOT_APPLIED.
- Structural target/history and weather are ready. The target has no qualifying personnel history; personnel_history sample_size=0.
- Injury coverage is connected but unapplied. Final inactives and starting OL/DL/secondary/QB are not verified.
- No prediction, TD probability, market price, or verified injury status should be inferred from this response.
- The API reports 855 combined structural holdout games, 8D MAE 10.79, winner accuracy 61.99%. Historical metrics are not a future guarantee or a composite score.

## Historical inventory snapshot

Earlier read-only reconciliation counted 7,383 historical games, 17,644 team pregame feature rows, 14,766 raw personnel snapshots, 7,447 TD outcomes, 2,378 historical analogs, 6,011 One Brain runs, 107 postgame reviews, 303,484 market snapshots, 51,910 temporal-memory rows, 2,382 research snapshots, 10,011 research signals, 89 game research states, and 1 prediction lock / 1 grade. TD research snapshots were 0. These are stored in Supabase, not copied here.

## Security and remaining level-up work

- Supabase Security Advisor previously flagged RLS disabled on 16 tables in private and yes_private schemas. No policy changes were applied; map least-privilege policies to actual server/client access before changing RLS.
- Protected sync functions require server-side, one-time credentials. Never guess, expose, or commit them.
- Recover the approved arena source from the Sites source workflow and check it into GitHub without visual changes.
- Close the source-status, personnel-history, and personnel-model pipeline gaps using authorized sync paths and traceable source records.
- Connect TD opportunity research, saved research, and parlay candidates to the same canonical game response; verify across surfaces.
- Define measurable factor criteria, then run regression, mobile/accessibility, source-freshness, and end-to-end checks before reporting a 9+ rating. No shared 9+ rubric is established yet.
