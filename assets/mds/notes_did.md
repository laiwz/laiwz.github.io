# Notes on New DiD Methods
--------------------------------

## _Get Estimators for DiD Designs Right_

Assume that the assumptions of **parallel trends** and **no anticipation** hold. So, the problem is about interpretations rather than identificaiton.

### When can the commonly used FE estimators be maintained?

- They are fine when ([dCDH 2022, p.4](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3980758)):
    1. treatment increases over time and is an absorbing state (often the case);
    2. treatment is binary;
    3. there is no variation in adoption timing.
  
  These are non-staggered designs with binary treatment and without covariates. FE estimators are unbiased for ATEs, in which treatment effects (TEs hereafter) are weighted by population.

- FE estimators can be problematic in other settings, because OLS places unreasonable weights on (likely) heterogeneous TEs, making FE estimators biased for usual causal parameters of interest (e.g., ATT, ATE). Examples for these settings include --
  1. Non-staggered, binary treatment, **with covariates/unbalanced panel**
      - Ironically, FE estimators collapse when we include unit-specific trends for _robustness_.<br>
  2. Non-staggered, continuous treatment
  3. Staggered, binary/continuous treatment

  FE estimators give negative weights to some TEs, leading to violations of "no sign reversal", i.e., if all individual TEs are identically signed, then the estimator should have the same sign. Even if there were no negative signs, weights may still be too different from population, making the FE estimator biased for, e.g., ATE. However, these concerns would not be consequential were TEs homogeneous (weighted average of a constant gives the same constant anyway!).
  
- It seems difficult to maintain FE estimators in most settings, as we often use staggered designs, almost surely include covariates, and are reluctant to assume TE homogeneity.

- To justify the use of FE estimators,  
