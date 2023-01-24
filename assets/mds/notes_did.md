# Notes on New DiD Methods
--------------------------------

## _Get Estimators for DiD Designs Right_

Assume that the assumptions of **parallel trends** and **no anticipation** hold. So, the problem is about interpretations rather than identificaiton.

### When can the commonly used FE estimators be maintained?

- They are fine when ([dCDH 2022, p.4](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3980758)):
    1. treatment increases over time and is an absorbing state (often the case);
    2. treatment is binary;
    3. there is no variation in adoption timing.
  
  These are non-staggered designs with binary treatment and without covariates. FE estimators are unbiased for ATEs, in which treatment effects are weighted by population.

- FE estimators can be problematic in other settings, because OLS places unreasonable weights on (likely) heterogeneous treatment effects, making FE estimators biased for usual causal parameters of interest (e.g., ATT, ATE). Examples for these settings include
  1. Non-staggered, binary treatmeng, **with covariates**
      - Ironically, FE estimators collapse when we include unit-specific trends for _robustness_.
  
