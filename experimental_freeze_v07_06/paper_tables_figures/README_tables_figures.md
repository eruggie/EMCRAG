# EMCRAG integrated M0–M1 and R0–R1 analysis

## Frozen inputs

- M0–M1 statistical summary: `/home/eugrug/Project_CRAG_MedGemma/benchmark_m0_m1/ragas_m0_m1_v07_03/response_relevancy_statistical_summary.csv`
- M0–M1 paired differences: `/home/eugrug/Project_CRAG_MedGemma/benchmark_m0_m1/ragas_m0_m1_v07_03/response_relevancy_paired_differences.jsonl`
- R0–R1 statistical summary: `/home/eugrug/Project_CRAG_MedGemma/benchmark_r0_r1/ragas_r1_v07_05/paired_analysis_r0_r1/R0_R1_statistical_summary.csv`
- R0–R1 paired differences: `/home/eugrug/Project_CRAG_MedGemma/benchmark_r0_r1/ragas_r1_v07_05/paired_analysis_r0_r1/R0_R1_paired_differences.csv`

## Cohorts

- M0–M1 paired observations: 193
- R0–R1 Response Relevancy paired observations: 194
- Four-system common Response Relevancy cohort: 191

## Figure captions

### Figure 1

Mean Response Relevancy for M0, M1, R0 and R1 on the common
four-system cohort. Error bars represent 95% non-parametric bootstrap
confidence intervals for the system-specific means.

### Figure 2

Overall paired effects of FT-10K. Points represent mean paired
differences and error bars represent 95% paired bootstrap confidence
intervals. Noise Sensitivity is sign-inverted in this figure only so
that positive values consistently indicate an advantage of the adapted
system.

### Figure 3

Direction-aware proportions of wins, ties and losses for the adapted
system. For Noise Sensitivity, lower values are treated as favorable.

### Figure 4

Paired scatter plot of standalone Response Relevancy scores for M0 and
M1. Points above the identity line favor M1; points below it favor M0.

### Figure 5

Paired R0–R1 scatter plots for the five RAGAS metrics. Points above the
identity line favor R1 for Context Precision, Context Recall,
Faithfulness and Response Relevancy. For Noise Sensitivity, points
below the identity line favor R1.

### Figure 6

Per-case comparison of the FT effect on Response Relevancy. The
horizontal axis represents M1−M0 and the vertical axis represents
R1−R0. Points above the dashed identity line indicate that the FT effect
was more favorable inside EMCRAG than in the standalone setting.
Crosses represent dataset-specific mean effects.

### Figure 7

Exploratory contrast between the pipeline and standalone FT effects:
(R1−R0)−(M1−M0). Positive values indicate that the effect was more
favorable inside EMCRAG. This analysis is post hoc and should be
reported as exploratory.

## Scatter-plot jitter

A deterministic Gaussian jitter with standard deviation
0.004 was used only to reveal overlapping observations.
All statistical analyses and exported source-data tables retain the
original exact scores.

## Statistical interpretation

The confirmatory analyses remain the separately prespecified paired
comparisons M0–M1 and R0–R1. The four-system common-cohort comparison
and the interaction contrast are descriptive or exploratory and should
not be presented as independently prespecified confirmatory tests.
