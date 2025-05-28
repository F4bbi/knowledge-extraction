# 📝 Paper Writing Guidelines for Authors

This guide outlines key principles to help authors avoid common pitfalls and meet the expectations of peer reviewers and the broader research community.

## 1. 🧪 Rigorous Experimentation

Many submissions fall short on experimental rigor—insufficient controls, lack of repeatability, vague protocol descriptions, or no statistical power analysis.

**Best-Practice Solutions:**

1. **Define Hypotheses & Variables**

    - State null and alternative hypotheses explicitly.
    - Identify independent, dependent, and control variables.

2. **Use Proper Controls & Randomization**

    - When possible, include both positive and negative controls.
    - Randomly assign subjects or data batches to conditions to avoid bias.

3. **Replicate & Report Variability**

    - Run ≥ 3 independent trials; report means ± standard deviations.
    - If variation exceeds \~5%, investigate sources before concluding.

4. **Perform Power Analysis**

    - Calculate required sample size up-front to detect your expected effect size (e.g., Cohen's d = 0.4).
    - Document alpha (commonly 0.05) and desired power (commonly 0.8).

5. **Pre-register & Share Protocols**

    - When journal or funder policies allow, register your design on platforms like OSF.
    - Include detailed methods (e.g., scripts, hardware specs) in supplements.

## 2. 📊 Comparison to Prior Work

Authors often claim novelty without fair, head-to-head benchmarks against the most relevant baselines.

**Best-Practice Solutions:**

1. **Conduct a Focused Literature Review**

    - Identify 3-5 seminal and recent papers tackling the same problem.
    - Highlight gaps your approach fills.

2. **Re-implement or Use Published Code**

    - Whenever possible, obtain or re-implement baseline methods rather than quoting old results.
    - Match preprocessing, hyperparameters, and evaluation metrics exactly.

3. **Present Results in Comparative Tables**

    | Method     | Dataset | Metric   | Result |
    | ---------- | ------- | -------- | ------ |
    | Proposed   | X       | Accuracy | 87.4 % |
    | Baseline A | X       | Accuracy | 82.1 % |
    | Baseline B | X       | Accuracy | 84.3 % |

    - Include confidence intervals or standard errors for each entry.

4. **Discuss Trade-Offs**

    - If your method improves one metric but worsens another (e.g., speed vs. accuracy), analyze why.
    - Be transparent about limitations relative to baselines.

## 3. 🔍 Quantitative Claims Need Proof

“20 % improvement” sounds impressive—until readers realize there's no reported variance, p-value, or context for that number.

**Best-Practice Solutions:**

1. **State Claims Early & Precisely**

    - In the Abstract/Introduction, quantify your main gain (e.g., “Our model reduces error by 20 %.”).

2. **Prove Them in the Results Section**

    - Show tabular or graphical results with error bars (95 % CI) or p-values.
    - Example:

        | Model    | Mean Error | 95 % CI      | p-value |
        | -------- | ---------- | ------------ | ------- |
        | Ours     | 0.12       | [0.10, 0.14] | 0.003   |
        | Baseline | 0.15       | [0.13, 0.17] | —       |

3. **Use Appropriate Statistical Tests**

    - T-tests, ANOVA, or non-parametric tests depending on distribution.
    - Correct for multiple hypotheses when reporting several metrics.

4. **Explain Practical Impact**

    - Beyond percentages, describe what a 20 % reduction means in domain terms (e.g., 2 days saved in processing time).

## 4. 📉 Dataset Size & Diversity

Too-small or homogenous datasets lead to overfitting and findings that don't generalize.

**Best-Practice Solutions:**

1. **Follow “Rule of Ten” When Feasible**

    - Aim for ≥ 10 samples per feature dimension (e.g., 50 features → ≥ 500 samples).

2. **Leverage Power-Based Sample Size Calculations**

    - For a medium effect (d = 0.4), two groups need \~100 samples each.

3. **Document Dataset Splits & Diversity**

    - Report train/validation/test sizes and demographic or source diversity (e.g., multiple sites, time periods).

4. **Augment When Necessary**

    - If real-world data are limited, consider data augmentation, transfer learning, or synthetic data—always flag these in methods.

5. **Assess Generalizability**

    Perform sensitivity analyses: how do results change if you drop 10-20 % of data or vary domain characteristics?

## 5. 🧭 Address Limitations of Key Method Components

Proposed methods often rely on critical components that may have inherent limitations. Failing to acknowledge these can undermine the robustness of the approach.

**Best-Practice Solutions:**

1. **Analyze and Discuss Limitations**

    - Explicitly address potential weaknesses of your method’s core components (e.g., “Early stopping based on validation error may fail if the validation set is small or unrepresentative”).

2. **Propose Mitigations or Alternatives**

    - Suggest ways to improve the component (e.g., “Using a larger validation set or incorporating uncertainty estimates could mitigate overfitting to the validation set”).

3. **Compare with Alternative Approaches**

    - If your method’s component is unconventional, compare it with alternatives (e.g., “Our safe set construction differs from [1] by using [X] instead of [Y], which may improve robustness in [specific scenario]”).

## 6. 📚 Justify Novelty Through Comprehensive Literature Review

Even if a method is simple or similar to existing approaches, its contribution must be clearly justified by demonstrating gaps in prior work.

**Best-Practice Solutions:**

1. **Map Your Work to Existing Literature**

    - Clearly state how your approach relates to prior work (e.g., “While [1] uses iterative training for label noise, our method introduces [X] to address [specific problem]”).

2. **Highlight Novel Contributions**

    - Emphasize what your method adds (e.g., “Our early stopping criterion is the first to incorporate [X], improving performance over [1] by [Y]%”).

3. **Cite Missing Relevant Work**

    - If prior work was overlooked, acknowledge it and explain how your method differs (e.g., “Although [1] proposed a similar safe set construction, our approach avoids [X] by [Y]”).

## 7. 🔍 Validate Claims with Comprehensive and Reproducible Experiments

Empirical claims must be supported by thorough, reproducible experiments that clearly demonstrate the method’s effectiveness and generalizability.

**Best-Practice Solutions:**

1. **Test on Diverse and Challenging Datasets**

    - Include datasets that reflect real-world conditions (e.g., “Clothing1M” for label noise studies) to demonstrate robustness.

2. **Use Clear and Reproducible Evaluation Metrics**

    - Ensure all metrics and baselines are well-defined and comparable (e.g., “Use clean validation sets for all methods to ensure fairness”).

3. **Provide Detailed and Visual Comparisons**

    - Use clear visualizations and summaries (e.g., scatterplots, tables with meaningful groupings) to support claims rather than overwhelming readers with raw data.

## 8. 📌 Clarify Definitions and Improve Readability

Ambiguous terms, undefined acronyms, and unclear explanations can hinder understanding and reduce the impact of the work.

**Best-Practice Solutions:**

1. **Define All Terms and Acronyms**

    - Clearly explain all technical terms and acronyms on first use (e.g., “SISR: Single Image Super-Resolution, HVS: Human Visual System”).

2. **Structure Complex Ideas Clearly**

    - Use well-organized explanations and avoid overly dense sections (e.g., “Reorganize Sec. 4.3 to clarify the concept of visual masking”).

3. **Use Visual and Tabular Aids to Improve Comprehension**

    - Avoid large, unstructured tables and use visual aids or summaries to highlight key findings
