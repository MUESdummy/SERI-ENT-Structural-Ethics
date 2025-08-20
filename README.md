# SERI v0.1 — Structural Ethics Readiness Index (ENT-Aligned)

**SERI v0.1** is an open framework and harness for evaluating the *structural ethics* of large language models (LLMs).  
It operationalizes **Emergent Necessity Theory (ENT)** by defining measurable, falsifiable indices that track how AI systems behave under recursion, adversarial drift, and containment stress.

This repository contains:
- ✅ The **SERI harness** (Python) — runs scenarios and produces JSON logs.
- ✅ A **JSON schema** for validating results.
- ✅ An academic **paper** (LaTeX + PDF) with framework + synthetic results.
- ✅ Example configs + replication checklist.

---

## 📖 Background

- **Emergent Necessity Theory (ENT)**: a systems-theoretic model proposing that adaptive systems collapse when coherence falls below a critical threshold.  
- **SERI** extends ENT into AI ethics by defining:
  - **RCI** — Recursion Containment Index  
  - **DSI** — Drift Susceptibility Index  
  - **HSM** — Hysteresis Safety Margin  
  - **SOR** — Symbolic Overreach Risk  
  - **ETT** — Externality Traceability Time  

Together, these measure whether an AI system maintains structural integrity, even under adversarial conditions.

---

## ⚙️ Installation

```bash
git clone https://github.com/yourname/seri-ent.git
cd seri-ent
pip install -r requirements.txt

```
Dependencies: numpy, matplotlib, jsonschema, jupyter
(Optional: transformers if you want to run real open-weight LLMs instead of the simulator.)




## < Usage >
Run a pilot scenario (adversarial Q&A, horizon 50, 200 runs, 5 seeds):
```
python seri_harness.py --scenario adversarial_qa --horizon 50 --seeds 42 43 44 45 46 --runs 200
```

Validate logs against the schema:
```
jsonschema -i results/*.json schema/seri_v0_1_log.schema.json
```

Analyze results and plot metrics:
```
jupyter notebook notebooks/analyze_results.ipynb
```

## 📊 Example Output (Synthetic)

| Setting         | RCI ↑ | DSI ↑ | HSM ↑ | SOR ↓ | ETT (s) ↓ |
|-----------------|-------|-------|-------|-------|-----------|
| EN, catch=0.80  | 0.81  | -0.0007 | 0.44 | 0.19 | 1.2 |
| AR, catch=0.60  | 0.55  | -0.0013 | **-0.05** | 0.33 | 2.1 |

- **EN** = English baseline  
- **AR** = Arabic, used as a non-dominant language stress-test  

---

## 📜 Paper

The research paper is included under `/paper`:
- **SERI\_Combined\_Framework\_Results.tex** — LaTeX source
- Explains the theory, methodology, simulator, synthetic results, and replication checklist.

## 🔒 Ethics Note

This framework is designed for **structural safety evaluation**, not for ranking commercial models.  
Logs are content-minimal (entropy, errors, timing) — no user data or sensitive content is stored.

---

##  Citation
(This Repo)

