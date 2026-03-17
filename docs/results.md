# Training Results — GAT Drug-Target Interaction

## Final Test Results

| Metric | Value |
|---|---|
| ROC-AUC | 0.7630 |
| Accuracy | 78.7% |
| Average Precision | 0.1848 |
| Binding recall | 59% |
| Random baseline | 0.5000 AUC |
| Parameters | 353,729 |
| Test pairs | 4,509 |

## Context

| Model | AUC | Uses protein features |
|---|---|---|
| Random | 0.500 | — |
| **This GAT model** | **0.763** | **No** |
| DeepDTA (published) | 0.880 | Yes |

This model uses only molecular graph features — no protein sequence
encoding. The gap to DeepDTA is explained by the missing protein
features, which is a clear direction for future improvement.

## Training details

- Dataset: DAVIS — 30,056 drug-target pairs
- Drugs: 68 molecules as molecular graphs
- Proteins: 442 kinase targets
- Train/Val/Test: 70/15/15 split
- Epochs: 50
- Device: NVIDIA T4 GPU (Google Colab)
- Best validation AUC: 0.7855

## Future improvements

- Add protein sequence encoding (CNN or transformer)
- Use larger dataset (BindingDB — 2M pairs)
- Add edge features to GAT convolutions
- Ensemble multiple GNN architectures
```

Commit:
```
# Training Results — GAT Drug-Target Interaction

## Final Test Results

| Metric | Value |
|---|---|
| ROC-AUC | 0.7630 |
| Accuracy | 78.7% |
| Average Precision | 0.1848 |
| Binding recall | 59% |
| Random baseline | 0.5000 AUC |
| Parameters | 353,729 |
| Test pairs | 4,509 |

## Context

| Model | AUC | Uses protein features |
|---|---|---|
| Random | 0.500 | — |
| **This GAT model** | **0.763** | **No** |
| DeepDTA (published) | 0.880 | Yes |

This model uses only molecular graph features — no protein sequence
encoding. The gap to DeepDTA is explained by the missing protein
features, which is a clear direction for future improvement.

## Training details

- Dataset: DAVIS — 30,056 drug-target pairs
- Drugs: 68 molecules as molecular graphs
- Proteins: 442 kinase targets
- Train/Val/Test: 70/15/15 split
- Epochs: 50
- Device: NVIDIA T4 GPU (Google Colab)
- Best validation AUC: 0.7855

## Future improvements

- Add protein sequence encoding (CNN or transformer)
- Use larger dataset (BindingDB — 2M pairs)
- Add edge features to GAT convolutions
- Ensemble multiple GNN architectures
