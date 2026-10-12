# Excluded artefacts

Dataset files and full FT/split parquet exports; Chroma store; model/base/adapter weights; tokenizer files; checkpoints; optimiser/RNG states; compiled caches; downloaded images; raw input manifests and clinical responses; raw retrieved/web evidence; diagnostic failures containing record/error detail; the manuscript; older notebooks, prototypes and development archives.

The excluded source artefacts remain untouched. Configurations and hashes identify required external resources. In particular, M1/R1 require the definitive adapter described in MODEL_CARD.md. The author-approved notebook set plus the recovered R0/R1 notebook is the public source selection.

The audit/ directory and SELECTION_REVIEW.md contain local preparation evidence and are ignored by Git. All public paths are allowlisted rather than selected by a recursive git add of the source tree.
