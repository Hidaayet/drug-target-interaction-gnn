# Drug-Target Interaction Predictor

A Graph Neural Network (GNN) that predicts whether a drug compound will bind
to a disease-causing protein target — the core computational problem in
drug discovery. Molecules are represented as graphs where atoms are nodes
and chemical bonds are edges.

---

## What it does

Given a drug molecule (as a SMILES string) and a protein target, the system:
1. Converts the molecule into a graph using RDKit
2. Encodes atom and bond features as node/edge attributes
3. Passes the graph through a Graph Attention Network (GAT)
4. Predicts binding affinity — will this drug bind to this target?

---

## Why this matters

Finding which drug molecules bind to disease-causing proteins is the
fundamental problem in drug discovery. Traditional lab screening takes
years and costs billions. AI can screen millions of candidates in seconds.

This is the same class of problem that:
- DeepMind's AlphaFold solved for protein structure
- Insilico Medicine uses to discover new drug candidates
- Schrödinger uses in computational drug design

---

## System overview

*Diagram coming soon*

---

## Tech stack

| Layer | Technology |
|---|---|
| Molecule processing | RDKit |
| Graph construction | PyTorch Geometric |
| Model architecture | Graph Attention Network (GAT) |
| Deep learning | PyTorch |
| Dataset | ChEMBL / BindingDB |
| Visualization | RDKit, Matplotlib |

---

## Project structure
```
drug-target-interaction-gnn/
├── data/
│   └── (download instructions in docs/SPEC.md)
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_molecule_graphs.ipynb
│   ├── 03_model_training.ipynb
│   └── 04_evaluation.ipynb
├── src/
│   ├── dataset.py
│   ├── model.py
│   └── train.py
├── docs/
│   └── SPEC.md
└── README.md
```

---

## Progress log

- [x] Project defined and documented
- [x] Data exploration
- [x] Molecule graph construction
- [x] GAT model training — AUC 0.7630
- [x] Evaluation and results
- [x] Molecular saliency visualization

---
##  Full Project Report

For detailed methodology, architecture, and results, see the **[complete project report](docs/DTI_GNN_Report (1) (Réparé).pdf)**.

---

## Author

**Hidayet Allah Yaakoubi**
Biomed Engineering student — Tunisia
