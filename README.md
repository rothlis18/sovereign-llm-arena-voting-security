# Sovereign LLM Arena: Enterprise Voting Pipeline Security Benchmark (17.11.26)

An automated multi-agent evaluation and satoshi (`sats`) state-ledger experiment testing **8 local Ollama models** in a full round-robin critique loop (`Generator` vs. `Validator`) across three systems-engineering lenses: **Conciseness**, **Technical Rigor**, and **Objectivity**.

## Experiment Overview
* **Date:** November 17, 2026 (`17.11.26`)
* **Prompt Domain:** Enterprise Voting System Security (database injection, ghost records, weight-allocation matrix manipulation, cryptographic hash-chains, consensus logging, append-only ledgers, and a 1–100 integer safety factor)
* **Total Test Cases:** 168 (`8 Generators × 7 Validators × 3 Lenses`)
* **Pass Threshold:** `OBJECTIVITY_SCORE >= 75`
* **Overall Run Health:** `168 PASS` | `0 FAIL` | `0 TIMEOUT ERRORS` *(First 100% completion run)*
* **Final Ledger Owner:** `mistral-nemo:12b` (`10,000 sats` valuation, `locked: true`)

---

## Leaderboard (Generator Performance)

| Rank | Generator Model | Passes | Fails / Errors | Avg Score | Peak Score | Avg Duration (s) |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **1** | **`phi4:latest`** | 21 / 21 | 0 | **87.43** | 100 | 191.29s |
| **2** | **`huihui_ai/qwen3-abliterated:8b`** | 21 / 21 | 0 | **86.38** | 100 | 127.60s |
| **3** | **`mistral-nemo:12b`** | 21 / 21 | 0 | **85.71** | 100 | 121.02s |
| **4** | **`qwen2.5-coder:14b`** | 21 / 21 | 0 | **84.43** | 100 | 204.26s |
| **5** | **`jaahas/gemma-2-9b-it-abliterated:latest`** | 21 / 21 | 0 | **84.24** | 100 | 122.42s |
| **6** | **`qwen2.5-coder:7b`** | 21 / 21 | 0 | **84.05** | 100 | 110.97s |
| **7** | **`llama3.2:3b`** | 21 / 21 | 0 | **83.62** | 95 | 78.63s |
| **8** | **`dolphin3:latest`** | 21 / 21 | 0 | **81.19** | 100 | 104.60s |

---

## Validator Strictness (Judge Behavior)

| Validator Model | Cases Judged | Avg Score Given | Fails / Errors Triggered |
| :--- | :---: | :---: | :---: |
| **`qwen2.5-coder:7b`** *(Strictest)* | 21 | **82.05** | 0 |
| **`llama3.2:3b`** | 21 | **82.24** | 0 |
| **`qwen2.5-coder:14b`** | 21 | **82.38** | 0 |
| **`mistral-nemo:12b`** | 21 | **82.62** | 0 |
| **`huihui_ai/qwen3-abliterated:8b`** | 21 | **83.95** | 0 |
| **`jaahas/gemma-2-9b-it-abliterated:latest`** | 21 | **85.43** | 0 |
| **`dolphin3:latest`** | 21 | **87.62** | 0 |
| **`phi4:latest`** *(Most Lenient)* | 21 | **90.76** | 0 |

---

## Key Engineering & Ledger Findings

1. **First Zero-Error, 100% Pass Run (`168/168`):**
   Unlike Day 1 (`165/168`) and Day 2 (`164/168`), every single Generator-Validator matchup passed without a single `600,000ms` timeout or sub-75 failure.
2. **Parser Edge-Case Resilience (`Case56` & `Case116`):**
   Both `phi4:latest` (`Case56`) and `llama3.2:3b` (`Case116`) triggered `"Critic emitted no parseable OBJECTIVITY_SCORE"` on Loop 1, but successfully self-recovered on Loop 2 to pass with scores of `85` and `92`.
3. **Divergent Risk Calibration (Safety Factor Spread):**
   * **Conservative / Pessimistic Models (`SF = 25–45`):** `mistral-nemo:12b` (`SF = 35`), `qwen2.5-coder:14b` (`SF = 30–45`), and `huihui_ai/qwen3-abliterated:8b` (`SF = 45`) modeled compounding pipeline failure probabilities and assigned low safety ratings.
   * **Optimistic Models (`SF = 85`):** `phi4:latest` and `qwen2.5-coder:7b` consistently assigned a safety factor of `85` assuming cryptographic controls function as specified.
4. **Metadata State-Leakage (`Case136`):**
   In `Case136`, `qwen2.5-coder:14b` again absorbed `"drift_score": 0.515` from the JSON ledger's `SELF_REFINEMENT` log into its response text, which `llama3.2:3b` flagged in its critique (`"some technical terms (e.g., 'drift score') could be defined"`).

---

## Repository Structure
```text
├── data/
│   ├── state_ledger_17_11_26.json      # Satoshi ownership & self-refinement drift log
│   └── benchmark_results_168.csv       # Full 168-case evaluation telemetry
├── outputs/
│   └── *.md                            # Individual Case1–Case168 markdown transcripts
├── scripts/
│   └── analyze_benchmark.py            # Telemetry parser & safety-factor extractor
└── README.md
```
