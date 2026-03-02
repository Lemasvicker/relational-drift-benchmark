[![DOI](https://zenodo.org/badge/1170621753.svg)](https://doi.org/10.5281/zenodo.18834343)

# Relational Drift Evaluation (RDE) Benchmark

**Author:** Victory Nlemadim  
**Version:** v1.0.0 (2026-03-02)

RDE is an evaluation suite for measuring **relationship-effects** (“Relational Drift”) in mental-health LLM responses using two metrics introduced in the accompanying preprint:

- **Relational Gravity (RG):** quantifies relationship-centralizing cues (availability absolutism, exclusivity, intimacy escalation, authority claiming, anthropomorphic bonding, contact-seeking).
- **Boundary Integrity (BI):** quantifies adherence to a user-defined **Support Contract** (relational boundaries).

This repository contains:
- a **300-item prompt set** (single-turn + multi-turn scripts),
- **Support Contract templates** (C1/C2/C3),
- an **annotation rubric** + labeling spreadsheet,
- and placeholders for **RG/BI scoring** code and evaluation scripts.

> ⚠️ Research use only. This does not provide medical advice or clinical care. If you or someone you know is in immediate danger, contact local emergency services.

---

## Contents

- `benchmark/` — RDE prompt set (JSONL + CSV)
- `contracts/` — Support Contract templates (C1/C2/C3) + constraint glossary
- `rubric/` — annotation guide + labeling template
- `rg_bi/` — (optional) scoring utilities (to be added)
- `eval/` — (optional) scripts to run models and summarize RG/BI (to be added)
- `examples/` — example model outputs and completed labels (to be added)

---

## Quickstart

### 1) Get the benchmark
- `benchmark/rde_prompts_v1_0.jsonl` (recommended for pipelines)
- `benchmark/rde_prompts_v1_0.csv`

Each item includes:
- `id`, `category`, `item_type` (`single` or `multiturn`)
- `support_contract_id` (C1/C2/C3)
- `prompt` and optional `script_user_turns`

### 2) Label outputs (human annotation)
Use `rubric/rde_labeling_template_v1_0.xlsx`:
1. Paste your model’s response into `assistant_response`
2. Assign `g1..g6` scores (0–3)
3. Mark boundary violations `v1..v8` (0/1) according to the contract
4. Rate helpfulness/warmth (1–5)
5. Export to CSV for analysis

### 3) Compute RG/BI
If you implement RG/BI as defined in the preprint, you can compute:
- category-wise means/medians
- multi-turn drift slopes (RG over turns)
- BI compliance rates by contract

---

## Support Contracts (C1–C3)
Contracts are stored in `contracts/` and represent user-selected relational boundaries.

- **C1:** Tool-like support (strict boundaries)
- **C2:** Warm coach (moderate boundaries)
- **C3:** Companion-leaning (non-exclusive)

---

## How to cite

### Cite the *dataset + benchmark release* (recommended)
Once you archive a release to Zenodo, include the Zenodo DOI here and cite that version.

**[Dataset]** Victory Nlemadim. *Relational Drift Evaluation (RDE) Benchmark v1.0.0*. Zenodo. DOI: `10.5281/zenodo.18834343`

### Cite the *preprint*
**[Paper]** Victory Nlemadim. *Relational Drift in Mental-Health LLMs: Metrics and Benchmarks for Bounded Empathy*. arXiv, 2026. arXiv:`XXXX.XXXXX`

> Tip: Zenodo supports **concept DOIs** (all versions) and **version DOIs** (specific releases). Use the *version DOI* for reproducibility.

---

## Recommended release workflow (free)
1) Publish the paper on **arXiv**.  
2) Archive this repo on **Zenodo** (GitHub→Zenodo integration) to mint a DOI per release.  
3) Optionally mirror the preprint on **OSF Preprints** for additional discoverability.

---

## License
- Dataset/prompts/rubric: **CC BY 4.0** (see `LICENSE-DATA`)  
- Code (if added): **MIT** (see `LICENSE-CODE`)

---

## Contributing
See `CONTRIBUTING.md`. New prompts, multilingual packs, and improved labeling guidance are welcome.

---

## Code of Conduct
See `CODE_OF_CONDUCT.md`.
