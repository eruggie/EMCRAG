# EMCRAG scientific source freeze

This release preserves EMCRAG v06.11 and FT-10K preparation, standalone M0/M1 inference/evaluation, R1 inference, paired R0/R1 evaluation and final figure production.

Nine historical notebooks are included. Only two code cells change: embedded Tavily literals are replaced with environment access. Selected non-distributable outputs are removed; prompts, parameters, paths, imports and order remain unchanged. Original/copy hashes and cell-level comparisons accompany the release.

The actual adapter is pinned by SHA-256 and documented; weights and full data are not distributed. M1/R1 end-to-end reproduction therefore requires external access. The recovered R0/R1 notebook closes the earlier scoring/statistics/figure-source gap; the original baseline bootstrap workflow remains unavailable. The original manuscript-stage Mann–Whitney/Holm/Cliff/Spearman section has been recovered and checked.

Static and citation checks passed; 18 pure numerical statistical comparisons matched archived summaries. All nine notebooks pass the official format schema after adding 11 deterministic non-executable cell ids. Every code source string and execution setting is unchanged by that repair. No training, complete notebook, GPU benchmark or paid API evaluation was run.

Author-owned code is Apache-2.0; data/model terms remain separate. A companion manuscript is maintained separately from the software release.
