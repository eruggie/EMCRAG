# Reproduction of the frozen experiments

## Scope and execution boundaries

This release preserves source rather than introducing path overrides or changing the experimental procedure. No complete notebook, training job, GPU benchmark or paid API evaluation was run during release preparation.

Use a separate WSL environment or machine with the historical directory layout. Do not create that layout by pointing public notebooks at the author's original project. Several cells overwrite artefacts, rebuild collections, or start paid evaluation.

## Required external artefacts

| Artefact | Historical location | Distribution |
| --- | --- | --- |
| Working project | /home/eugrug/Project_CRAG_MedGemma | Recreate in an isolated environment |
| Hugging Face cache | /mnt/f/hf_home_cache | Obtain authorised model access separately |
| Chroma index | /mnt/f/chroma_db_store | Reconstruct; not included |
| IMB full data | /mnt/f/processed_datasets/IMB_Dataset_Arrow/IMB_Dataset_Safe | Authorised upstream access required |
| Curated IMB test set | /mnt/f/processed_datasets/IMB_Curated_Test_Set_1000 | Not included; exact construction source not established |
| Historical IMB MCQA | /mnt/f/processed_datasets/IMB-MCQA/Dataset_Arrow | Used in index preparation history |
| MMMED Italian | /mnt/f/processed_datasets/MMMED/Italian | Authorised upstream access and image rights required |
| FT-10K adapter | Studio output path in MODEL_CARD.md | Identified by hash but not distributed |

The exact bytes of images used in archived R0 are unavailable; later M0/M1 shared frozen image bytes. Access to current image URLs does not establish historical image identity.

## Environment and credentials

See [DEPENDENCIES.md](DEPENDENCIES.md). Export `TAVILY_API_KEY` and `OPENAI_API_KEY` before launching Jupyter. `.env.example` documents variable names only: these notebooks do not automatically load a .env file. Authenticate separately with Hugging Face for gated resources. GitHub credentials are not needed to execute the selected notebooks.

Never put real keys in notebook source or output. Example:
```bash
export TAVILY_API_KEY='replace-in-your-private-shell'
export OPENAI_API_KEY='replace-in-your-private-shell'
```

## 1. Index preparation

Inspect Knowledge_Injection.ipynb before selecting cells. Cell 5 indexes DART; cells 9–10 contain historical collection rebuilding. Analisi_Chroma_DB_Local.ipynb cell 4 renames the old internal collection to internal_knowledge_backup_old and promotes external_knowledge (IMB-QA) to internal_knowledge. These operations are destructive to an existing index and must only be used in the isolated reconstruction.

The current inspected index uses cosine space with 384-dimensional multilingual MiniLM vectors. The retained indexing source does not explicitly pin all current collection configuration. The current index is not a checksum-verified snapshot of the July benchmark. Corpus exclusions and reconstruction order remain a limitation.

## 2. EMCRAG and R0

CRAG_MedGemma_v.06.11.ipynb cells 6–16 define/load the models, retriever, router and graph. Cell 10 contains the shared generator and cleaning functions. Cell 11 has retrieval default top_k=4; cell 15 explicitly calls top_k=3. Keep both unchanged.

Cells 25–38 contain the dataset preparation and baseline runner sections, including alternative calibration/extended paths. The final RAGAS run is ragas_v0611_20260719T010434Z (196 evaluated records). Cells 41–50 contain evaluation/export/plotting. Inspect the saved run configuration before choosing cells; it is not safe to execute all alternative runner sections sequentially.

R0 evaluation used RAGAS 0.2.5, GPT-4o and text-embedding-3-small. New cloud evaluations incur charges and are not byte-reproducible. Archived numerical scores are supplied; the raw clinical cases and retrieved/web texts are not.

## 3. FT data preparation and Studio training

EMCRAG_FT_v.07.01_DataPrep_Pilot.ipynb implements deterministic category-stratified splits with seed 20260831 and excludes the 1000 curated test records. Cell 28 exports nested SFT datasets, including 10000 training examples. Historical pilot and FT5K diagnostic cells remain in place; they do not describe the definitive training job.

The definitive training took place in Unsloth Studio. [MODEL_CARD.md](MODEL_CARD.md) and model/training_config.json record the actual run rather than an invented training script. Uploaded training/validation files match the project exports by SHA-256. Obtain upstream permissions before redistributing training records or the adapter.

## 4. Standalone M0/M1

EMCRAG_Prepare_Inputs_196.ipynb prepares the shared manifest and images from pinned R0 exports. Its required raw exports are not distributed.

EMCRAG_M0_M1_Standalone_Benchmark_v07_03.ipynb cell 4 loads only the generator source from v06.11, and cell 6 defines standalone inference. Subsequent cells start M0/M1 generation and establish completion gates. M1 requires the exact definitive adapter hash.

Sanitising v06.11 changes its whole-notebook hash but not the generator-source hash. The standalone inference contract records the whole-notebook hash and refuses a conflicting existing contract. Keep archived outputs/contracts untouched and put a reconstruction in a separate workspace; do not silently change historical gates to resume an archived run with changed provenance.

## 5. Standalone evaluation

EMCRAG_M0_M1_RAGAS_v07_03.ipynb provides paid Response Relevancy evaluation. Cell 15 performs the paired numerical analysis: 193 complete pairs, 20000 bootstrap resamples, base bootstrap seed 20260831. Cell 3's earlier bootstrap seed is superseded by cell 15; it is not the final analysis seed.

## 6. Adapted pipeline and evaluation

EMCRAG_R1_Benchmark_v07_04.ipynb cell 9 loads the definitive adapter; cell 16 disables it for visual expansion and enables it for final generation. Cell 28 defines the resumable 196-case runner. The notebook also retains inherited alternative baseline/evaluation cells: follow the R1 section rather than running everything.

EMCRAG_R0_R1_RAGAS_v07_05.ipynb:
- cells 2–7: R1 canonical inputs and paid metric evaluation;
- cell 9: paired R0/R1 statistics, 10000 bootstrap resamples, base seed 20261006;
- cell 11: integrated tables and figures from archived score/difference files.

R1 uses refreshed evidence. Only 61/194 paired context sets match R0, so this is not a controlled evidence replay isolating the adapter.

## 7. Numerical re-analysis without model/API execution

The supplied per-record scores and paired differences support local numerical re-analysis. The paired-statistics sections read score files; figure preparation reads the supplied paired summaries/differences. Run these sections only after inspecting their inputs and providing required imports/constants in an isolated historical layout. Do not run evaluation cells merely to analyse existing scores.

The final effect scatter uses the 191-case four-system intersection, retaining overlapping points without a fitted regression. Other raw-score scatter plots use deterministic display-only jitter. Keep original numerical source data unchanged.

## Remaining limits

A complete end-to-end reconstruction was not tested. Missing raw cases, historical R0 images, exact curated-test construction and index freeze prevent a claim of bitwise repeatability. A historical manuscript-stage source excerpt for Mann–Whitney, Holm, Cliff's delta and stratified Spearman is provided under analysis/. The complete original baseline bootstrap workflow remains unavailable; v06.11's saved summary contains exploratory normal-approximation intervals instead. The recovered R0/R1 notebook closes the earlier paired-statistics and figure-source gaps.

## Notebook format caveat

The historical M0/M1 RAGAS notebook declared format 4.5 but 11 cells lacked ids. The release now adds deterministic non-executable ids, recorded in CODE_CELL_COMPARISON.json. Cell source, order, execution counts and metadata dictionaries are unchanged. All nine release notebooks pass the official schema; the original whole-file hash remains recorded alongside the normalised copy.
