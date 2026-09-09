<div align="center">

# 🫁 Cancer-Survival-KG · Lung-Cancer Survival Prediction

**Does a knowledge graph + GNN add value beyond a simple clinical model for lung-cancer survival prediction?**

![Survival](https://img.shields.io/badge/Survival%20Analysis-1F3864?style=for-the-badge)
![All of Us](https://img.shields.io/badge/All%20of%20Us%20RW-2E7D32?style=for-the-badge)
![GNN](https://img.shields.io/badge/HeteroGraphSAGE--Cox-8E44AD?style=for-the-badge)
![PyTorch](https://img.shields.io/badge/PyTorch%20Geometric-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)

</div>

---

This project extends a heterogeneous knowledge-graph framework over **All of Us** data to time-to-event survival prediction in **379 lung-cancer patients (60 observed deaths)**. We enrich the graph with 26 time-aware clinical features across 0-, 6-, and 12-month cumulative windows and compare three survival models using the same patient cohort, shared 5-fold splits, and Cox-based evaluation:

1. **Tabular Cox** — clinical features + age/sex, without graph structure.
2. **Intermediate GNN** — closely matched clinical and demographic information represented as a graph and processed with a HeteroGraphSAGE-Cox encoder.
3. **Full KG-GNN** — the intermediate graph extended with the broader genomic, geographic, and social determinants of health (SDoH) context.

**Key finding:** the regularized **Tabular Cox model achieved the highest mean performance across all three time windows**. In this cohort, neither representing the clinical information through graph message passing nor adding the broader multimodal KG context improved mean predictive performance.

<p align="center">
  <img
    src="https://github.com/user-attachments/assets/8cff86cd-a0ed-4a9a-ace9-974970eeccb3"
    width="800"
    alt="HeteroGraphSAGE-Cox architecture"
  />
</p>

This README summarizes the project's final workflow and main results. The main analysis notebook contains the full code organized by project stage, together with outputs that could be shared without exposing participant-level data. Full scientific background, methodology, results, and interpretation are provided in the submitted final project report.

## ⚙️ Running the code

This project was developed inside the **All of Us Researcher Workbench**. Participant-level data cannot be exported or redistributed, so this repository contains code only and no participant-level data. The notebook assumes the workspace bucket / mounted data paths described within it (`WORKSPACE_CDR`, `WORKSPACE_BUCKET`, or the Researcher Workbench 2.0 local mount path).

## 🗂️ Repository contents

**`Lung_survival_analysis_Amit_&_Or.ipynb`** — the final analysis notebook. It follows the project's stages in order:

1. **Genomic tabular baseline** — initial logistic-regression baselines using variant-level and person-level genomic features.
2. **Binary survival smoke test** — an early GNN classifier using a fixed survival threshold, evaluated across repeated seeds.
3. **Knowledge-graph survival pipeline** — cohort/death audit, lung-cancer subgraph construction, and clinical-feature enrichment at 0/6/12-month windows.
4. **Landmark analysis** — a sensitivity analysis that re-anchors prediction to later time points rather than the original lung-cancer reference date.
5. **Intermediate GNN** — a reduced graph containing clinical and demographic information for comparison with the tabular baseline.
6. **Tabular Cox baseline** — the clinical variables represented without graph structure.
7. **Final comparison** — shared 5-fold cross-validation across all three models:

| Model | Harrell C-index (0m / 6m / 12m) | IPCW C-index (0m / 6m / 12m) |
|---|---|---|
| **Tabular Cox** | 0.696±0.066 / 0.768±0.041 / 0.754±0.047 | 0.667±0.085 / 0.706±0.113 / 0.726±0.119 |
| Intermediate GNN | 0.677±0.062 / 0.632±0.063 / 0.630±0.059 | 0.658±0.095 / 0.621±0.085 / 0.647±0.112 |
| Full KG-GNN | 0.665±0.104 / 0.653±0.111 / 0.660±0.106 | 0.638±0.118 / 0.624±0.112 / 0.625±0.110 |

## 👥 Team

**Or Brener** · **Amit Mizrahi**  
Supervisor: **Dr. Alon Bartal**  
Knowledge-graph foundations: **Ofek Mendel**
