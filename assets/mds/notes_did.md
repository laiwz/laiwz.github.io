# Notes on New DiD Methods
--------------------------------

## _Get Estimators for DiD Designs Right_

Assume that the assumptions of **parallel trends** and **no anticipation** hold. So, the problem is about interpretations rather than identificaiton.

### When can the commonly used FE estimators be maintained?

- They are fine when ([de Chasemartion and D'Haultfœuille 2022, p.4](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3980758)):
    1. treatment increases over time and is an absorbing state (often the case);
    2. treatment is binary;
    3. there is no variation in adoption timing.
  
  These are non-staggered designs with binary treatment and without covariates. FE estimators are unbiased for ATEs, in which treatment effects (TEs hereafter) are weighted by population.

- FE estimators can be problematic in other settings, because OLS places unreasonable weights on (likely) heterogeneous TEs, making FE estimators biased for usual causal parameters of interest (e.g., ATT, ATE). Examples for these settings include ---
  1. non-staggered, binary treatment, **with covariates/unbalanced panel** ([Borusyak et al 2022, Section 5.2](https://arxiv.org/abs/2108.12419))
      - Ironically, FE estimators collapse when we include unit-specific trends for _robustness_.
  2. non-staggered, continuous treatment ([de Chasemartion et al 2022](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4011782))
  3. staggered, binary/continuous treatment

  FE estimators give negative weights to some TEs, leading to violations of "no sign reversal", i.e., if all individual TEs are identically signed, then the estimator should have the same sign. Even if there were no negative signs, weights may still be too different from population, making the FE estimator biased for, e.g., ATE. However, these concerns would not be consequential were TEs homogeneous (weighted average of a constant gives the same constant anyway!).
  
- It seems difficult to maintain FE estimators in most settings, as we often use staggered designs, almost surely include covariates, and are reluctant to assume TE homogeneity.

- To justify the use of FE estimators, one has to corroborate that
    1. the weighting scheme is not too bad: no negative weights so the no sign reversal porperty holds; it seems impossible to argue that the weights happen to be those forming an ATE...
        - [Goodman-Bacon 2021](https://www.sciencedirect.com/science/article/abs/pii/S0304407621001445)
        - [Jakiela 2021](https://arxiv.org/abs/2103.13229)
        - [Sun and Abraham 2021](https://www.sciencedirect.com/science/article/abs/pii/S030440762030378X) (for event studies)
        - [de Chasemartion and D'Haultfœuille 2022](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3980758)
    2. TEs are homogenous
        - [Jakiela 2021](https://arxiv.org/abs/2103.13229)
        - [de Chasemartion and D'Haultfœuille 2020](https://www.aeaweb.org/articles?id=10.1257/aer.20181169): two statics to provide a sense on how heterogeneous TEs are so that FE estimators are not informative in presence of negative weights
    
    I guess even if these tests provide some support for maintaining FE estimators, the results would only be informative by in the directional/qualitative sense. So, alternative robust estimators are needed.
    
### Robust Estimators
