# Weighted vs. Unweighted Link Prediction in Bipartite Networks

This work was part of the Network Science Class at FCUP Porto.

Link prediction estimates the likelihood of future or missing 
connections in a network based on its observed structure. This project 
investigates whether incorporating edge weights into traditional 
structural scores improves link prediction performance in a bipartite 
network setting — and whether this holds when scores are used both as 
standalone ranking methods and as input features for supervised 
classifiers.

## Project overview

Four commonly used structural scores were computed in both weighted 
and unweighted forms:

| Score | Type |
|-------|------|
| Preferential Attachment | Neighbourhood-based |
| Shortest Path | Path-based |
| Local Path (LP) | Path-based |
| L3 | Path-based |

These scores were evaluated in two ways:
1. **Independently** — as ranking scores for candidate links
2. **As features** — combined as input to supervised classifiers 
   (Logistic Regression, KNN, XGBoost)

## Key findings

- **Preferential Attachment** performed best among standalone scores 
  and showed no sensitivity to edge weights
- **Shortest Path** showed a minor performance improvement when 
  weight-adjusted
- **Local Path and L3** yielded a score of 0 for all negative samples 
  and 50% of positive samples due to network sparsity, effectively 
  reducing them to binary features
- **XGBoost** marginally outperformed other classifiers in 2 of 3 
  test folds
- **KNN** was the only classifier negatively affected by the 
  integration of weights; Logistic Regression and XGBoost were 
  unaffected
- **Feature importance** highlighted Preferential Attachment and L3 
  as most relevant; Local Path contributed minimally — likely an 
  artefact of sparsity causing LP and L3 to capture redundant 
  information
- Overall conclusion: weighted versions of traditional scores do not 
  significantly improve link prediction performance in bipartite 
  network settings

## Limitations & future work

- Results are specific to a single bipartite network; generalisability 
  to other graph types (e.g. directed, heterogeneous) is not 
  established
- Network sparsity heavily influenced the behaviour of path-based 
  scores and may have obscured meaningful weight effects
- Future work should explore broader graph types, refined weighting 
  schemes, and more advanced validation techniques

## Repository structure

| File | Contents |
|------|----------|
| `Network_Science_Final_Project.pdf` | Paper describing the analysis and results |
| `Final_Project_NS.ipynb` | Notebook with the full code (explanations and analysis are provided in the paper) |
| `samples/` | Samples that were used for the computations |

## Dependencies
Key packages: `networkx`, `numpy`, `pandas`, `scikit-learn`, 
`xgboost`, `matplotlib`, `seaborn`
