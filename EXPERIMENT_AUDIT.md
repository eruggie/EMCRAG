# Experimental provenance and release audit

## Verified identities

The frozen manuscript SHA-256 is ab6f7479bba1306d106488646fff4c628d9e5d816605aa511502790ffc416c49; the source-local and supplied Drive copies match. The manuscript is unchanged and not redistributed.

Original v06.11 notebook SHA-256:
6f842c4658a1d70a1a9a864d438c243c3b1af3ee47fdf6fd5ac5d7d1594e74a1.

Generator source (cell 10, id dabb732b) SHA-256:
703c7e3fddfcd9b0e0fdbacf1049ba4d58de9540cae589f21e20e91bd7989189.

Recovered R0/R1 notebook SHA-256:
036f87b7fe7bf843229324783c3b6601e1c793038158a5b5f2760081180650fd.

It was zero bytes during the first audit and became a 12-cell notebook after the author saved it from VS Code. This is an author-supplied source update, not a release edit. Cells 9 and 11 recover paired statistics and integrated figure generation.

Forty frozen manifest/hash assertions passed in the initial audit. Detailed copy checks and cell comparisons are supplied in [VALIDATION_REPORT.json](VALIDATION_REPORT.json) and [CODE_CELL_COMPARISON.json](CODE_CELL_COMPARISON.json).

## Settings versus defaults

| Setting | Located source/evidence | Finding |
| --- | --- | --- |
| Base generator | v06.11 cell 8 | google/medgemma-1.5-4b-it |
| Evaluator | cell 9 | Qwen2.5-3B-Instruct-GGUF, q4_k_m |
| Embedding | cell 11 | paraphrase-multilingual-MiniLM-L12-v2 |
| top-k | cell 11 default 4; cell 15 call 3 | The actual pipeline call agrees with paper top-k=3 |
| Distance | cell 11 | 0.55 |
| Router | cell 14 | -0.50 and +0.75 on [-1,1] |
| Configured generation budget | cell 10 and contracts | 2048; up to 512 new tokens; greedy |
| R0 judging | frozen run manifest | RAGAS 0.2.5; GPT-4o; text-embedding-3-small |
| Standalone bootstrap | M0/M1 RAGAS cell 15 | 20000; seed 20260831 supersedes earlier seed |
| Pipeline bootstrap | R0/R1 RAGAS cell 9 | 10000; seed 20261006 |
| Definitive training | extracted Studio config and trainer metadata | Matches the principal FT-10K settings in the manuscript |

R1 scoring cell 4 configures a 4096-token judge output allowance to avoid incomplete judge responses. This is a judge configuration, not a change to generator decoding; the paper does not specify that allowance. No exact cloud judge snapshot is pinned.

## Results and cohort checks

Saved baseline scores have 196 records: 100 IMB and 96 MMMED. Faithfulness has 195 valid scores; Noise Sensitivity has 193. Archived paired summaries reflect 193 standalone pairs, 194 pipeline precision/recall/relevance pairs, and 191 pipeline Faithfulness/noise pairs.

Independent comparison of canonical records confirms 194 identical questions/references; 61 identical context sets and 133 different sets, including 132 cases with R0 web evidence. Figure source data confirm 191 common cases (98 IMB, 93 MMMED), with 123 points above the identity line. Main means, intervals and p-values agree with the manuscript's rounded values.

The effect scatter in R0/R1 notebook cell 11 directly uses exact paired deltas, preserving overlap. Display-only jitter applies to other raw-score plots. The figure manifest's generic jitter field must not be read as evidence of jitter in every figure.

## Unresolved discrepancies and limitations

1. Baseline bootstrap source: v06.11 cell 47 (id 2a1c9227), source lines 352–368, computes exploratory normal intervals rather than bootstrap intervals. After review, the manuscript-preparation history yielded the original section computing Mann–Whitney/Holm, Cliff's delta and stratified Spearman statistics. See analysis/SOURCE_RECOVERY.json and the verbatim excerpt. A CPU check reproduces the rounded Faithfulness Cliff's delta and the reported Holm significance bound. This partially closes the provenance gap; it does not recover the original bootstrap workflow or change any historical result.
2. Stale Markdown labels: v06.11/R1 first cell names v06.10. These labels remain historical.
3. v06.11 cell 8 describes 2048 as a model maximum; [official MedGemma documentation](https://huggingface.co/google/medgemma-1.5-4b-it) describes a larger capacity. The experiment used a configured 2048 budget.
4. Historical analysis prose generally says 10000 bootstrap resamples and describes retrieval as frozen. The final standalone source/results use 20000, and 133 supplied context sets differ. The historical prose is not included as authoritative release interpretation.
5. Current Chroma metadata corroborates cosine space and IMB-QA collection lineage after the documented rename, but no archived July index checksum was identified. Exact corpus reconstruction/exclusions are not attested.
6. Training and project dependency snapshots differ. The versions are recorded separately, not reconciled by changing historical code.
7. Full notebook SHA-256 changes after Tavily sanitisation. Historical contracts keep experimental identities; the generator-cell hash remains unchanged. Standalone code rejects a conflicting existing inference contract.
8. Curated-test construction and historical R0 image-byte identity remain incomplete. Raw records and trained weights are withheld, limiting end-to-end reproduction.

## Changes permitted in this release

Only v06.11 cell 13 and R1 cell 14 (both id 0cd2a8c2) change code, replacing the credential literal with environment access. Cell order, prompts, parameters, paths and imports are unchanged. Output removals are recorded separately with cell and output-block locations. No clinical dataset records or downloaded images are redistributed.

This audit does not establish absolute code originality or the absence of similarity to external implementations.

## Notebook metadata normalisation

EMCRAG_M0_M1_RAGAS_v07_03.ipynb declared nbformat 4.5 but 11 cells lacked ids. During the author-approved pre-publication checks, deterministic ids were added as non-executable metadata. No source string, prompt, parameter, import, path, output or execution count changed in this operation. All nine notebooks now pass the official schema. Original and release hashes and every id addition are recorded in CODE_CELL_COMPARISON.json.
