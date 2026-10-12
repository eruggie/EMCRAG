# EMCRAG

## Abstract

The rapid adoption of generative AI systems in the healthcare sector requires maintaining an adequate level of confidentiality to safeguard patient privacy and, on the other, developing streamlined systems that enable deployment on local edge hardware, thereby eliminating the need to rely on the cloud-based systems of major global AI providers. This paper describes Edge Medical Corrective RAG (EMCRAG) developed for Italian medical question answering, utilizing a compact multimodal LLM running on local hardware. The corrective RAG algorithm is used to improve the robustness of the generation by combining vision-guided query augmentation, local evidence retrieval, corrective routing, conditional web recovery and token-aware generation. A separate RAGAS benchmark distinguished semantic quality from operational failures. Evaluation revealed focused retrieval for corpus-aligned textual questions, but weaker support for image-centred questions; topical answers could remain insufficiently grounded. An additional experimental setup involved a separate RAGAS evaluation, replacing the original MedGemma generator node with a version obtained through fine-tuning on an isolated subset of the Italian medical dataset. This benchmark did not show substantial improvements: standalone relevance deteriorated, while the adapted pipeline showed stronger textual grounding. Changed external evidence limits attribution of this gain to the adapter alone. The research demonstrates a feasible, inspectable local workflow on edge devices but future developments require clinical validation by expert physicians.

## Independent research on EMCRAG

This repository is the public research home of **Edge Medical Corrective RAG (EMCRAG)**, developed by **Eugenio Ruggieri**, Independent Researcher, Prato, Italy ([ORCID](https://orcid.org/0009-0000-3014-3545)). It brings together the implementation, experimental data, benchmark measurements and statistical analyses for Italian medical question answering on local hardware.

EMCRAG combines vision-guided query augmentation, local retrieval, corrective routing, conditional web recovery and token-aware generation. The research examines both the behaviour of this pipeline and the effect of adapting its final MedGemma generator through FT-10K supervised fine-tuning.

Four experimental systems are represented: **M0**, the base standalone generator; **M1**, the FT-10K adapted standalone generator; **R0**, the base EMCRAG pipeline; and **R1**, EMCRAG with the adapter enabled only for final generation. The visual expansion node remains unadapted. R0 and R1 used different external evidence, which limits attribution of their differences to the adapter alone.

The versioned research implementation is available at tag [`v1.0.0`](https://github.com/eruggie/EMCRAG/tree/v1.0.0).

## Repository structure

```text
EMCRAG/
├── *.ipynb                         EMCRAG, input preparation and benchmark workflows
├── Chroma_DB/                      Knowledge ingestion and index inspection notebooks
├── ragas_results/                  R0 scores, summaries and run manifests
├── benchmark_m0_m1/                Standalone inference contracts and paired evaluation data
├── benchmark_r0_r1/                R1 scores and paired R0/R1 statistical results
├── experimental_freeze_v07_06/
│   └── paper_tables_figures/       Integrated tables, figures and numerical figure data
├── fine_tuning/v07_01/             Dataset preparation manifests and diagnostic reports
├── model/                         Adapter configuration and definitive training metadata
├── analysis/                      Baseline statistical source excerpt and supporting results
├── REPRODUCIBILITY.md              Detailed execution sequence and required inputs
├── DEPENDENCIES.md                 Recorded software environments
├── MODEL_CARD.md                   FT-10K training and adapter identification
├── EXPERIMENT_AUDIT.md             Experimental configurations and interpretation limits
├── THIRD_PARTY_NOTICES.md          Dataset, model and software attribution
└── CITATION.cff                    Software citation metadata
```

### Implementation notebooks

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

## Experimental data and measurements

The repository provides per-record numerical RAGAS scores, paired differences, statistical summaries, inference contracts, run manifests and the numerical data underlying the figures. Baseline evaluation comprises 196 cases: 100 IMB textual questions and 96 Italian MMMED image-plus-text questions. Missing metric scores are excluded per analysis without imputation; paired sample sizes therefore differ across metrics.

Measurements cover Context Precision, Context Recall, Faithfulness, Response Relevancy and Noise Sensitivity. Standalone M0/M1 evaluation focuses on Response Relevancy. Paired analyses include bootstrap intervals, Wilcoxon tests and rank-biserial effects. Tables and figures are available under `experimental_freeze_v07_06/paper_tables_figures/`.

Full source datasets, clinical question/answer records, retrieved text, images, vector indexes and model weights are obtained separately. The FT-10K adapter is identified and documented in [MODEL_CARD.md](MODEL_CARD.md), but its weights are not distributed here. Numerical re-analysis and complete model-based reproduction consequently have different input requirements.

## Replicating the research

Start with [REPRODUCIBILITY.md](REPRODUCIBILITY.md) for the cell-level workflow and [DEPENDENCIES.md](DEPENDENCIES.md) for the recorded environments.

1. **Prepare an isolated environment.** Use WSL2/Ubuntu with the documented Python and GPU dependencies. The notebooks use historical absolute paths; recreate the required directory layout in a separate research environment.
2. **Obtain the external inputs.** Arrange authorised access to IMB, DART, Italian MMMED and the required base models. Consult [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for their separate terms. Exact M1/R1 reproduction also requires the definitive FT-10K adapter described in the model card.
3. **Configure services.** Export `TAVILY_API_KEY` and `OPENAI_API_KEY` before starting Jupyter; [.env.example](.env.example) lists the variables. Authenticate separately with Hugging Face for gated models. Web recovery and cloud RAGAS evaluation require external services and may incur charges.
4. **Construct the retrieval index and run R0.** Follow the selected ingestion and collection-management sections in `Chroma_DB/`, then the model, graph, baseline inference and evaluation sections of `CRAG_MedGemma_v.06.11.ipynb`.
5. **Prepare and evaluate adaptation.** Use the FT data-preparation notebook for the category-stratified training/validation splits. The definitive training was performed in Unsloth Studio; its configuration is recorded under `model/`. Prepare the shared evaluation inputs, run standalone M0/M1 inference and evaluate their paired scores.
6. **Evaluate the adapted pipeline.** Run the R1 benchmark sections, followed by R1 metric evaluation and the paired R0/R1 statistics and integrated figure sections in `EMCRAG_R0_R1_RAGAS_v07_05.ipynb`.
7. **Re-analyse the published numerical results.** Use the supplied score and paired-difference files with the statistical and figure-generation sections. These analyses do not require generating new model responses or requesting new API evaluations. Inspect cell dependencies and input paths before running individual sections.

The notebooks contain alternative experimental and diagnostic sections; follow the documented sequence instead of executing every cell sequentially. Complete end-to-end repeatability is limited by unavailable raw inputs, historical R0 image identity, the exact curated-test construction, the original index snapshot and the undistributed adapter. The complete original baseline bootstrap workflow is also unavailable. See [REPRODUCIBILITY.md](REPRODUCIBILITY.md) and [EXPERIMENT_AUDIT.md](EXPERIMENT_AUDIT.md) for the implications. The experimental measurements do not constitute clinical validation.

## Licence and citation

Author-owned code and documentation are licensed under [Apache-2.0](LICENSE). Dataset, model and third-party terms apply separately, including to any subsequent adapter distribution; see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

Use [CITATION.cff](CITATION.cff) to cite EMCRAG, specifying the version or commit used. Please also cite the underlying datasets, models and methods relevant to your experiment.
