<img width="676" height="404" alt="regularDB" src="https://github.com/user-attachments/assets/162f9807-6733-4436-a886-c1242429eed0" />
<img src="/home/himanshu/Downloads/rergularDB_animated_pipeline.svg" width="100%"/>
# regularDB

> A curated, standardized, and benchmarked compendium of regulatory genomic datasets for Type 2 Diabetes (T2D) research.

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-active%20development-orange.svg)]()
[![Assays](https://img.shields.io/badge/assays-5-green.svg)]()
[![Models](https://img.shields.io/badge/LLM%20models-6-purple.svg)]()

---

## Overview

**regularDB** is an R package that systematically curates and provides programmatic access to public regulatory genomics databases relevant to Type 2 Diabetes (T2D). It enables researchers to discover, access, and benchmark epigenomics datasets — removing the barrier between biologists and high-quality regulatory data.

The database curation pipeline uses a **multi-LLM benchmarking approach** to systematically identify, validate, and score public databases across five major epigenomics assay types.

---

## Assay Coverage

| Assay | Status | Runs Complete |
|---|---|---|
| ATAC-seq | In progress | 1 / 3 |
| ChIP-seq | Pending | 0 / 3 |
| CUT&RUN | Pending | 0 / 3 |
| DNA Methylation | Pending | 0 / 3 |
| RNA-seq | Pending | 0 / 3 |

---

## Curation Methodology

Database curation follows a three-phase pipeline:

**Phase 1 — Systematic Compilation**
Six large language models (LLMs) are queried using five standardized prompt strategies to identify candidate databases for each assay type. All models receive identical prompts to ensure comparability.

**Phase 2 — Reproducibility & Hallucination Testing**
Each prompt is run three times per model at temperature = 0. Databases are scored by consistency across runs:

- Appears in 3/3 runs → high confidence
- Appears in 2/3 runs → moderate confidence
- Appears in 1/3 runs → likely hallucinated

**Phase 3 — Manual Validation**
Surviving databases are verified for URL validity, data accessibility, metadata quality, and T2D relevance before inclusion in the package.

---

## LLM Benchmark Panel

| Model | Developer | Query Method |
|---|---|---|
| Qwen | Alibaba | Manual |
| GLM5 | Zhipu AI | Manual |
| MiniMax-M2.7 | MiniMax | Manual |
| Gemini 3.1 | Google | Manual |
| Claude Opus 4.6 | Anthropic | API |
| GPT-4o | OpenAI | API |

---

## Prompt Strategies

Each model is queried using five prompt engineering strategies:

1. **Zero-shot instruction** — direct instruction with output format constraints
2. **Few-shot format control** — example-guided output formatting
3. **Role-based precision boost** — bioinformatics expert persona framing
4. **Guided filtering (chain-of-thought)** — step-by-step reasoning over database properties
5. **Gap detection** — identifying databases absent from a known seed list

---

## Repository Structure

```
regularDB/
├── ATACseq_DBs/          # Raw LLM outputs for ATAC-seq (3 runs × 6 models)
├── ChIPseq_DBs/          # Coming soon
├── CUTandRUN_DBs/        # Coming soon
├── DNAmethylation_DBs/   # Coming soon
├── RNAseq_DBs/           # Coming soon
├── LICENSE
└── README.md
```

Each assay folder contains CSV files per model per run, named as:

```
{Model}_{Assay}_Run{N}.csv
```

---

## R Package

The regularDB R package (in development) will provide:

- `search_databases()` — query curated databases by assay type, tissue, or disease
- `get_metadata()` — retrieve standardized metadata for any listed database
- `benchmark_db()` — score database quality across QC, accessibility, and annotation metrics
- Direct access wrappers for major databases (GEO, ENCODE, CMDGA, PanKbase, HPAP, etc.)

---

## Citation

If you use regularDB in your research, please cite:

> Bha, H. et al. (2026). regularDB: A curated compendium of regulatory genomic datasets for T2D research. *In preparation.*

---

## License

This project is licensed under the [Apache License 2.0](LICENSE).

---

## Contact

**BDB-Genomics** · [GitHub](https://github.com/BDB-Genomics)
