# Third-party attribution and licence scope

## EMCRAG code

Apache-2.0 applies to author-owned EMCRAG source and new release documentation. It does not replace dataset licences, model terms or rights in third-party material. Numerical study outputs are author-produced results and are distributed under Apache-2.0 to the extent the author holds rights in them; no dataset questions, answers, web passages or images are included as standalone data artefacts.

The notebooks integrate existing algorithms and libraries. Algorithm use and library imports are evidenced; derivation from a specific external source file has not been established. This is not an exhaustive similarity audit.

## Research methods

The manuscript credits Lewis et al. (2020), Retrieval-Augmented Generation; Yan et al. (2024), Corrective Retrieval Augmented Generation; Dettmers et al. (2023), QLoRA; and Es et al. (2024), RAGAs. Bootstrap, Mann–Whitney, Holm correction, Cliff's delta, Spearman correlation and Wilcoxon tests are established methods, not claims of new EMCRAG algorithms.

[Corrective RAG paper](https://arxiv.org/abs/2401.15884) · [RAG paper](https://arxiv.org/abs/2005.11401) · [QLoRA paper](https://arxiv.org/abs/2305.14314) · [RAGAs paper](https://aclanthology.org/2024.eacl-demo.16/).

The author's frozen manuscript acknowledges assistance from Gemini, ChatGPT and Codex for coding/review and language work. Scientific decisions and interpretation remain attributed to the author.

## Datasets and models

| Resource | Attribution | Terms and source |
| --- | --- | --- |
| IMB | Romano, Riccio, Barone, Postiglione and Moscato, University of Naples Federico II | [CC BY-NC-ND 4.0; gated](https://huggingface.co/datasets/praiselab-picuslab/IMB) |
| DART | Barone, Laudante, Riccio, Romano, Postiglione and Moscato | [CC BY 4.0; gated](https://huggingface.co/datasets/praiselab-picuslab/DART) |
| MMMED | Riccio, Romano, Barone, Orlando, Russo, Postiglione, La Gatta and Moscato | [CC BY-NC 4.0; gated](https://huggingface.co/datasets/praiselab-picuslab/MMMED) |
| MedGemma 1.5 | Google; Sellergren and colleagues | [HAI-DEF terms](https://developers.google.com/health-ai-developer-foundations/terms) |
| Qwen2.5-3B-Instruct-GGUF | Qwen/Alibaba Cloud | [Qwen Research licence](https://huggingface.co/Qwen/Qwen2.5-3B-Instruct-GGUF/blob/main/LICENSE) |
| Multilingual MiniLM | Sentence Transformers | [Apache-2.0 model card](https://huggingface.co/sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2) |

The official DART card specifies CC BY 4.0; a second contradictory hyperlink pasted in a message does not change the upstream licence statement. Dataset access conditions remain applicable. Image URLs in MMMED do not establish redistribution rights in all downloaded image files.

Adapter and processor configs under model/ identify MedGemma-derived artefacts and are documented subject to upstream model terms rather than an unrestricted Apache grant. No weights or tokenizer/chat-template files are included. HAI-DEF model distribution requires the agreement, restrictions and appropriate notice; see the upstream terms before a future adapter release.

## Libraries

These are runtime dependencies, not vendored libraries. Consult the licence shipped with the exact version being used; current upstream checks are recorded below.

| Component | Upstream licence/source |
| --- | --- |
| LangGraph | [MIT](https://github.com/langchain-ai/langgraph/blob/main/LICENSE) |
| LangChain | [MIT](https://raw.githubusercontent.com/langchain-ai/langchain/master/LICENSE) |
| Chroma | [Apache-2.0](https://raw.githubusercontent.com/chroma-core/chroma/main/LICENSE) |
| RAGAS | [Apache-2.0](https://github.com/vibrantlabsai/ragas/blob/main/LICENSE) |
| Transformers | [Apache-2.0](https://raw.githubusercontent.com/huggingface/transformers/main/LICENSE) |
| PEFT | [Apache-2.0](https://raw.githubusercontent.com/huggingface/peft/main/LICENSE) |
| TRL | [Apache-2.0](https://raw.githubusercontent.com/huggingface/trl/main/LICENSE) |
| OpenAI Python | [Apache-2.0](https://raw.githubusercontent.com/openai/openai-python/main/LICENSE) |
| llama-cpp-python | [MIT](https://raw.githubusercontent.com/abetlen/llama-cpp-python/main/LICENSE.md) |
| SciPy | [BSD terms](https://raw.githubusercontent.com/scipy/scipy/main/LICENSE.txt) |
| Unsloth library / Studio | [Apache-2.0 library; Studio components identified as AGPLv3](https://github.com/unslothai/unsloth/blob/main/LICENSE) |

Using Studio for training is distinguished from copying Studio's source. No Studio program code is redistributed. Tavily Python 0.7.23 declares MIT in the installed distribution's licence classifier. Direct upstream licence URLs examined during preparation were unavailable. The installed-package evidence and other dependency declarations are recorded in DEPENDENCY_LICENCES.json. No Tavily SDK source is included here.

Other imported packages retain their own terms: PyTorch, datasets, sentence-transformers, NumPy, pandas, scikit-learn, Matplotlib, Pillow, Gradio, requests, psutil and monitoring helpers. They are external dependencies, not included in the Git release.
