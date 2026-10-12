# EMCRAG

Edge Medical Corrective RAG for Italian medical question answering.

This repository preserves the source used for EMCRAG v06.11, the FT-10K data-preparation workflow, standalone M0/M1 inference and evaluation, and the R0/R1 pipeline comparison. It preserves the research implementation and numerical evaluation artefacts developed by Eugenio Ruggieri. A companion manuscript is maintained separately.

The scientific source freeze is identified by tag `v1.0.0`. See [RELEASE_STATUS.md](RELEASE_STATUS.md) for the release scope.

## Components

| Component | Notebook |
| --- | --- |
| EMCRAG v06.11, baseline runner and R0 RAGAS | [CRAG_MedGemma_v.06.11.ipynb](CRAG_MedGemma_v.06.11.ipynb) |
| Frozen 196-case input preparation | [EMCRAG_Prepare_Inputs_196.ipynb](EMCRAG_Prepare_Inputs_196.ipynb) |
| FT dataset preparation and historical diagnostics | [EMCRAG_FT_v.07.01_DataPrep_Pilot.ipynb](EMCRAG_FT_v.07.01_DataPrep_Pilot.ipynb) |
| Standalone M0/M1 inference | [EMCRAG_M0_M1_Standalone_Benchmark_v07_03.ipynb](EMCRAG_M0_M1_Standalone_Benchmark_v07_03.ipynb) |
| Standalone RAGAS and paired statistics | [EMCRAG_M0_M1_RAGAS_v07_03.ipynb](EMCRAG_M0_M1_RAGAS_v07_03.ipynb) |
| Adapted EMCRAG inference | [EMCRAG_R1_Benchmark_v07_04.ipynb](EMCRAG_R1_Benchmark_v07_04.ipynb) |
| R1 RAGAS, paired R0/R1 statistics and integrated figures | [EMCRAG_R0_R1_RAGAS_v07_05.ipynb](EMCRAG_R0_R1_RAGAS_v07_05.ipynb) |
| Dataset acquisition and indexing | [Knowledge_Injection.ipynb](Chroma_DB/Knowledge_Injection.ipynb) |
| Historical collection inspection and rename | [Analisi_Chroma_DB_Local.ipynb](Chroma_DB/Analisi_Chroma_DB_Local.ipynb) |

M0 is Google MedGemma without an adapter; M1 uses FT-10K. R0 is archived EMCRAG with the base final generator; R1 enables FT-10K only in final generation. The upstream visual expansion remains base-only.

## What is preserved

The notebook code, parameters, prompt strings, paths and cell order remain historical. The only executable-source changes replace two embedded Tavily credentials with environment-variable access. Eleven missing non-executable Jupyter cell identifiers are normalised in the standalone RAGAS notebook; all cell source and execution settings remain unchanged. Selected outputs containing dataset examples, medical responses or recovered web material have been removed. Numerical evaluation outputs and figures remain available where suitable for redistribution. [CHANGELOG.md](CHANGELOG.md), [RELEASE_MANIFEST.csv](RELEASE_MANIFEST.csv) and [CODE_CELL_COMPARISON.json](CODE_CELL_COMPARISON.json) provide the audit trail.

## Reproduction

Start with [REPRODUCIBILITY.md](REPRODUCIBILITY.md) and [DEPENDENCIES.md](DEPENDENCIES.md). The notebooks retain absolute WSL paths; this is an archival source release rather than a portable installation package. Do not run all cells indiscriminately or run copies against a valuable existing project/index.

The full datasets, downloaded images, vector index, raw medical input/output records, base-model weights and adapter weights are not distributed. [MODEL_CARD.md](MODEL_CARD.md) identifies the definitive adapter and the remaining distribution decision. Full M1/R1 reproduction requires access to that adapter.

[EXPERIMENT_AUDIT.md](EXPERIMENT_AUDIT.md) distinguishes verified configurations and results from incomplete historical provenance. A manuscript-stage source excerpt for Mann–Whitney, Holm, Cliff's delta and stratified Spearman analysis has been recovered and checked; the complete original baseline bootstrap workflow remains unavailable. Statistical verification is not a clinical validation.

## Licensing and citation

Author-owned EMCRAG code and release documentation are licensed under [Apache-2.0](LICENSE). Dataset, model and third-party rights remain separate; see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md). The Apache licence does not make the dataset or trained adapter freely redistributable.

Use [CITATION.cff](CITATION.cff) to cite the software, together with the exact scientific tag/commit after publication. Cite the underlying models, datasets and methods as listed in the attribution document.
