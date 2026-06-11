# Route Scoreboard: UAVM Smoke Fill

This scoreboard is example-only and uses local historical records. It is not a current CodaBench ranking audit.

| route_id | stage | paradigm | role | evidence_surface | best evidence | run_id | config_path | seed_or_fold | command_or_script | artifact | status | next action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reloc3r-official-full-epoch | L1/L3 | P3 direct RPR | leaderboard mainline | hidden_official | `final_score=0.003188`, `distance=0.002528`, `angle=0.003849` | official_metric_full_epoch_v1_20260506_045442 | recorded in source memory | not recorded in smoke fill | official test inference script in source memory | result.zip + result.txt row/hash record | anchor | protect as baseline |
| reloc3r-angle-improvement | L2/L3 | P3 + selective angle correction | candidate | bounded/design | Phase42 says next spec is rank1 angle improvement feasibility | phase42-macro-route-decision | phase42 decision record | not applicable | not applicable | phase42 memory/report | candidate | structural/spec gate before execution |
| roma-dense-field | L1 | P1/P2 dense correspondence | source/control | bounded | bounded dense field positive vs sparse controls | local historical route records | not restated | not restated | not restated | source memory records | held/source | use as geometry/correspondence evidence |
| mast3r-geometry-field | L1/L2 | P6 geometry field | angle source | bounded | bounded 2048 geometry field strong angle signal | local historical route records | not restated | not restated | not restated | source memory records | held/source | use in selective/hybrid route only |
| vggt-geometry-field | L1/L2 | P6 geometry field | distance/source control | bounded | bounded geometry field strong distance signal, weak angle | local historical route records | not restated | not restated | not restated | source memory records | held/source | combine or hold |
| roma-mast3r-vggt-hybrid | L1/L2 | P1/P2/P6 hybrid | mechanism evidence | bounded/diagnostic | source complementarity positive; full hybrid not promoted | exp-20260509-roma-mast3r-vggt-hybrid-v1 | not restated | not restated | not restated | experiment record | hold | do not submit full three-source fusion |
| madpose-official | L1 | P5 geometry solver | wildcard/control | bounded | adapter alive but bounded proxy negative | local historical route records | not restated | not restated | not restated | source memory records | reject/hold | redesign only if raw conventions solved |
| sacpose-official-style | L1/L2 | P2 correspondence-aware RPR | structural candidate | smoke/bounded | official chain worked but exact migration weak | local historical route records | not restated | not restated | not restated | source memory records | hold_redesign | reopen only with range/distance redesign |
| grelpose-frozen-head | L1 | P2/RPR-like external route | negative control | bounded | Phase48 bounded head red | phase48-grelpose-pairuav-head-smoke | phase48 spec/plan | not restated | train_phase48_head.py in source record | phase48 report/memory | reject | do not package or submit |

## Decision Surface Notes

- `role` is necessary because not every strong source is a submission route.
- `evidence_surface` must say whether the score is hidden official, public leaderboard, local full eval, bounded eval, smoke, or diagnostic.
- `run_id`, `config_path`, `seed_or_fold`, `command_or_script`, and `artifact` should be filled when available; missing fields make the route provisional for fresh decisions.
- `next action` prevents route drift from turning every held route into an implementation task.
