# 🫁 Lung Cancer Survival Prediction

**Senior Bioinformatics Project — Bar-Ilan University**  
**Amit Mizrahi & Or Brener**  
Bartal Lab, Bar-Ilan University · In collaboration with University of Miami researchers

## Overview

This project explores lung-cancer survival prediction using clinical and biological data from the **All of Us Research Program**.

We extended an existing heterogeneous cancer knowledge-graph framework to a time-to-event survival setting and compared three approaches:

1. **Tabular Cox model** — clinical features with age and sex.
2. **Intermediate GNN** — comparable clinical and demographic information represented as a graph.
3. **Full KG-GNN** — the graph extended with broader genomic, geographic, and social-determinants-of-health context.

The final cohort included **379 lung-cancer patients**, with **60 observed death events**. Clinical information was represented across cumulative 0-, 6-, and 12-month windows.

## Main Result

Across the primary evaluation, the regularized **Tabular Cox model achieved the strongest overall performance**, outperforming the graph-based models. The project highlights an important practical lesson: additional model complexity does not necessarily improve prediction when the dataset is relatively small and highly censored.

## Methods & Technologies

- Python
- Survival analysis and Cox proportional-hazards modeling
- Graph Neural Networks (GNNs)
- Heterogeneous Knowledge Graphs
- HeteroGraphSAGE-Cox
- Machine learning
- Patient-level stratified 5-fold cross-validation
- Harrell C-index and IPCW C-index
- Kaplan–Meier risk-stratification analysis
- All of Us Researcher Workbench

## Data Privacy

Patient-level **All of Us** data cannot be exported or redistributed. This public repository is intended to contain only material that can be shared without exposing participant-level information or restricted data.

## Repository Contents

The cleaned project notebook and additional public project materials will be added here after a final privacy and reproducibility review.

## Project Context

This work was completed as a senior B.Sc. Bioinformatics project at Bar-Ilan University, as part of a broader research collaboration involving Bartal Lab and University of Miami researchers.
