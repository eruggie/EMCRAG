# Recorded environments

The two requirements files are historical environment snapshots, copied without edits. They are not a newly tested dependency lock or a guarantee that every package can be installed on a fresh machine. In particular, a development torchaudio build and GPU-specific packages require an appropriate package source and compatible CUDA/toolchain.

| Setting | Evidence |
| --- | --- |
| R0 evaluation Python | Extended manifest: 3.11.14 |
| RAGAS | 0.2.5 |
| Numerical analysis | numpy 2.4.2, pandas 3.0.0, scipy 1.17.0 |
| Project Transformers / TRL | requirements snapshots: 4.57.6 / 0.24.0 |
| Project Unsloth | requirements snapshots: 2026.2.1 |
| Definitive training Transformers / TRL | Studio adapter README: 5.5.0 / 0.23.1 |
| Definitive training PyTorch / PEFT | 2.10.0+cu130 / 0.18.1 |
| Definitive training datasets / tokenizers | 4.3.0 / 0.22.2 |

Training, inference and judging environments must be recorded separately. Do not merge the snapshots into a fabricated single environment.

Principal imports include Unsloth, Transformers, PyTorch, PEFT, datasets, Chroma, llama-cpp-python, LangGraph, LangChain Hugging Face/OpenAI integrations, sentence-transformers, Tavily, OpenAI, RAGAS, NumPy, pandas, SciPy, scikit-learn, Matplotlib, Pillow, Gradio, psutil and GPU monitoring helpers. Jupyter is needed to inspect/run notebooks.

The release preparation uses only JSON/AST checks and limited CPU numerical verification. No dependency installation, model loading or GPU compatibility test has been carried out. Eighteen archived statistical groups were checked using extracted original pure functions on CPU, including their configured bootstrap repetitions; all matched the saved summaries.
