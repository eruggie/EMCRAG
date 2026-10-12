# Release preparation record

## Scientific source freeze v1.0.0

- Preserved nine selected notebooks and their historical cell order, source, prompts, paths and parameters.
- Replaced the embedded Tavily literal with os.environ["TAVILY_API_KEY"] in v06.11 cell 13 and R1 cell 14, both id 0cd2a8c2. os was already imported, so no import changes were needed.
- Removed selected output blocks containing dataset/medical/web examples. Preserved numerical summaries, statistical outputs and harmless figures.
- Included author-approved frozen score artefacts, paired differences, manifests, summaries and precomputed scientific figures.
- Added British English documentation, licence scope, citation, environment-variable example and audit trail.
- Identified the definitive Google-base adapter and excluded the earlier Unsloth-base project copy.
- Read the author-resaved R0/R1 notebook after the earlier zero-byte state. Its inclusion recovers pipeline statistics and final figure source.

No refactoring, functional correction, parameter change, path rewrite, model/API run, training or benchmark execution was carried out.

See RELEASE_MANIFEST.csv for original/copy checksums and CODE_CELL_COMPARISON.json for exact cell changes and output removals. Removed credential values are deliberately not present in the change record.

## Approved pre-publication follow-up

- Added deterministic ids to 11 cells of EMCRAG_M0_M1_RAGAS_v07_03.ipynb to satisfy nbformat 4.5. This is a non-executable format repair; all source and execution settings are unchanged.
- Recovered the original manuscript-stage baseline statistics section from project history, retained it verbatim as a documented excerpt, and checked its numeric outputs on CPU.
- Updated English documentation to distinguish recovered rank-test/effect-size provenance from the still-unavailable bootstrap workflow.
- The author-approved implementation and its recorded non-functional additions are preserved in the released source. Earlier preparation history is retained in a private local recovery archive.

## Neutral release metadata

Release naming, citation metadata and public source provenance use neutral software identifiers. The public Git history starts at this neutral scientific source snapshot. All nine notebook files are byte-identical to the reviewed implementation snapshot; only release documentation/provenance and checksum inventories change in this operation.
