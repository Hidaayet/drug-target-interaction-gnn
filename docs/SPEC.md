# Project Specification — Drug-Target Interaction Predictor

**Author:** Hidayet Allah Yaakoubi
**Date:** March 2026
**Status:** In progress

---

## 1. Project summary

A Graph Neural Network that predicts drug-target interactions (DTI) —
whether a drug molecule will bind to a disease-causing protein. Drug
molecules are converted into molecular graphs using RDKit, then processed
by a Graph Attention Network (GAT) that learns which atoms and bonds are
most important for binding.

---

## 2. Goals

- Build a complete DTI prediction pipeline from raw data to predictions
- Implement a Graph Attention Network from scratch using PyTorch Geometric
- Achieve above 80% ROC-AUC on the test set
- Visualize molecular attention weights — which atoms the model focuses on
- Produce clean, documented, reproducible code

---

## 3. Dataset — BindingDB

| Property | Value |
|---|---|
| Source | BindingDB — bindingdb.org |
| Size | ~2 million drug-target pairs |
| Drug format | SMILES strings |
| Target format | Protein sequences (UniProt IDs) |
| Labels | Binding affinity (Ki, Kd, IC50) |
| Task | Binary classification — binds / does not bind |

**Binarization rule:**
- Binding affinity ≤ 1000 nM → positive (binds) → label 1
- Binding affinity > 1000 nM → negative (does not bind) → label 0

---

## 4. Molecule representation

Drug molecules are represented as graphs:
- **Nodes** = atoms (features: atomic number, degree, charge, aromaticity)
- **Edges** = chemical bonds (features: bond type, conjugation, ring)

Example: Aspirin (C9H8O4)
- 13 atoms → 13 nodes
- 13 bonds → 26 directed edges (bidirectional)

SMILES → RDKit → molecular graph → PyTorch Geometric Data object

---

## 5. Model architecture — Graph Attention Network (GAT)
```
Input: molecular graph
    ↓
GAT Layer 1 — 8 attention heads × 8 features = 64 features per node
    ↓
GAT Layer 2 — 8 attention heads × 8 features = 64 features per node
    ↓
GAT Layer 3 — 1 attention head × 64 features
    ↓
Global mean pooling — aggregate all node features into one vector
    ↓
Fully connected layers → sigmoid → binding probability (0–1)
```

**Why GAT over GCN:**
- Attention weights show which atoms matter most for binding
- Different neighbors contribute differently (not equal weighting)
- Interpretable — we can visualize attention on the molecule

---

## 6. Features

**Node features (per atom):**
- Atomic number (one-hot encoded, top 44 elements)
- Degree (number of bonds)
- Formal charge
- Number of hydrogens
- Is in ring
- Is aromatic
- Hybridization type

**Edge features (per bond):**
- Bond type (single, double, triple, aromatic)
- Is conjugated
- Is in ring

---

## 7. Training strategy

- Train/val/test split: 70/15/15
- Optimizer: Adam, lr=0.001
- Loss: Binary cross entropy
- Batch size: 64 graphs
- Epochs: 50
- Early stopping: patience 10

---

## 8. Evaluation metrics

| Metric | Description |
|---|---|
| ROC-AUC | Primary metric — discrimination ability |
| Accuracy | Overall correct predictions |
| Precision/Recall | Per-class performance |
| F1 score | Harmonic mean of precision and recall |

---

## 9. Development phases

| Phase | Description | Tools |
|---|---|---|
| 1 | Data exploration | Pandas, RDKit, Matplotlib |
| 2 | Molecule graph construction | RDKit, PyTorch Geometric |
| 3 | GAT model training | PyTorch, PyTorch Geometric |
| 4 | Evaluation | scikit-learn, Matplotlib |

---

## 10. Dataset download instructions

1. Go to bindingdb.org/bind/chemsearch/marvin/Download.jsp
2. Download "BindingDB_All.tsv.zip" (full database)
3. Extract and place BindingDB_All.tsv in data/
4. Do not commit to GitHub (see .gitignore)
