# Recovered manuscript-stage baseline statistics

The verbatim statistics section in baseline_manuscript_statistics_excerpt.txt was recovered from the recorded file-add operation for the author's manuscript-preparation script. SOURCE_RECOVERY.json identifies the source and the exact excerpt hash. It is an original historical section, not newly generated statistical code.

The complete retrieved section computes dataset-level means, Mann–Whitney U tests, Cliff's delta, Holm correction across five metrics and pooled/within-dataset Spearman correlations. It belongs to manuscript preparation and must not be presented as part of the original v06.11 inference notebook.

The excerpt relies on imports and globals defined earlier in its original script: pandas/NumPy/SciPy, json/hashlib, the original scores dataframe f, dataset labels styles, plot_data, DATA and ROOT. It is retained as a .txt provenance fragment rather than falsely advertised as a complete standalone executable. The full document-building file was not retrieved. No document-building dependencies or private chat transcript are redistributed.

A CPU-only check of the excerpt on the pinned released baseline scores reproduces the manuscript's Faithfulness Cliff's delta when rounded to three decimals. The original bootstrap workflow has not been recovered; the excerpt does not implement bootstrap intervals. The released v06.11 notebook's exploratory normal intervals are unchanged.
