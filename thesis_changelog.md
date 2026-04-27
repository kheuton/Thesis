# Thesis Feedback Changelog

---

## 1. Decision problem definitions
- [ ] Formally define the decision problem solved by each experiment.

## 2. Surrogate usage specification
- [ ] Formally document (ideally as a table) how each surrogate is used per experiment, specifying for each: whether hyperparameters are **fixed** or **tuned on a validation set via decision loss**.
- [ ] For any claim that hyperparameter tuning improves performance, add a head-to-head comparison of the **same surrogate with fixed hyperparameters vs. validation-tuned hyperparameters**.

## 3. Overfitting diagnostics
- [ ] Report both **decision training error** and **prediction training error** for each surrogate (alongside existing test metrics) to make overfitting visible.

## 4. Interpolation Figure Revision (Figure 6 in Standalone Chapter)

### 4a. Extend the loss-landscape sweep
- [ ] Plot $t \cdot \theta_{PG} + (1 - t) \cdot \theta_{DPO}$ for $t$ **outside** $[0, 1]$ (not just the interpolation interval) to show the broader loss landscape.
- [ ] Add vertical lines marking where the chosen parameters ($\theta_{PG}$, $\theta_{DPO}$, and any selected operating point) sit on the sweep.

### 4b. Hyperparameter reporting on the figure
- [ ] If the plot shows a single run, annotate **which hyperparameters were used** — in particular, flag the value of $h$ for the PG loss, since a large $h$ explains divergence between decision loss and surrogate loss.

### 4c. Consistent y-axis normalization
- [ ] If normalizing the y-axis, apply the **same transformation across both subplots** so their scales are directly comparable.

### 4d. Interpolation hyperplane
- [ ] Consider replacing the two 1D plots with a single 2D visualization: the **hyperplane formed by the affine combination of $\theta_{PG}$, $\theta_{DPO}$, and $\theta_{SPO+}$**, showing decision loss (and/or surrogate loss) as a surface or heatmap over that plane.

---

## Change log

| Item | Change | Location in thesis |
|------|--------|--------------------|
| Short LoF/LoT captions | Added `[short]` argument to 15 figure/table captions so List of Figures and List of Tables show first sentence only, not the full caption | `bpr/{table1,table2}.tex`, `daml/sections/{intro_figure,results_synth1D,frontier_figure}.tex`, `daml/supp_sections/{supp_real_data,supp_metrics_table}.tex`, `dpo/{fig_benchmark_bump,sec_expt_budget,sec_expt_portfolio,sec_expt_topK,fig_triple_synth,fig_triple_synth_regret,app_synth,fig_topK_interp_6panel}.tex` |
| Citation whitespace | Added a space before every citation command directly attached to the previous character (legacy of docx→tex conversion) | `bpr/{introduction,methods,discussion}.tex`, `supplementary/ch3_bpr.tex` |
| Citations before periods | Moved citations from after sentence-ending periods to before them (canonical academic style) | Same 4 BPR-related files |
| Removed table highlighting | Stripped all `\hl{}` from BPR Tables 1 & 2 — highlighting was inconsistent and undocumented; bolding still encodes "best / overlaps best" | `bpr/{table1,table2}.tex` |
| Supplement reference | Replaced "(details in the supplement)" with `Sec.~\ref{gaussian-process-models}` linking to the GP subsection in Ch. 3 supp. | `bpr/methods.tex` |
| Bibliography: ZIGP entry | Added `year = {2022}` to `heutonZIGP2022`; consolidated 3 duplicate entries (`heutonPredictingSpatiotemporalCounts2022`, `heuton_predicting_2022`) into this one canonical entry | `refs/thesisbib.bib`, `daml/sections/{background,intro}.tex` |
| Bibliography: Hengl entry | Consolidated 3 duplicate entries for "Spatial sampling and resampling" into `hengl_spatial_2022` (the one with author + year) | `refs/thesisbib.bib`, `bpr/methods.tex` |
| BPR acknowledgements hidden | Commented out `\input{content/chapters/bpr/acknowledgements}` so per-chapter acknowledgements no longer appear in the build | `thesis_main.tex` |
| Citation → chapter reference | Replaced "Heuton et al. [2024]" textual citation with `Chapter~\ref{chap:bpr}~\citep{...}` parenthetical | `daml/sections/results_opioid.tex` |
| BPR gain → real-world counts | Added parentheticals translating BPR improvements into concrete outcomes (≈27 more overdoses reached on Cook County, <5 on MA, ≈8 more birds observed on Cranes) using denominators 683.5/512.5/167.7 | `daml/sections/{results_opioid,results_birds}.tex` |
| Abstract refinement | Softened "this objective is misaligned with decision quality" to "can be misaligned … when the model is misspecified or data is insufficient" | `content/abstract.tex` |
| Intro: training description | Reworded: "trained to minimize the error … in these heldout years" → "trained to minimize the error … in the training data (using a metric like mean squared error), and it is hoped that it will generalize well to these heldout years" | `content/introduction.tex` |
| Intro: misalignment caveat | Added "when the model is misspecified" qualifier to the claim that misaligned objectives lead to worse decisions | `content/introduction.tex` |
| Intro: chapter overviews | Updated Chapter 3 / 4 / 5 bullet items to highlight venues: AJE publication (Ch. 3), ICML 2025 (Ch. 4), AISTATS 2025 OPTIMAL workshop (Ch. 5) | `content/introduction.tex` |
| Chapter 4 venue note | Added two-line note at start of DAML chapter pointing to the ICML 2025 publication and the public code repository | `thesis_main.tex` |
| Intro grammar fix | "can enable inform data-driven decisions" → "can inform data-driven decisions" | `daml/sections/intro.tex` |
| Code footnote disabled | Commented out the `\ifdefined\ispreprint` footnote block (was duplicating the URL footnote in thesis context) | `daml/sections/intro.tex` |
| Methods Rank styling | Changed `\paragraph{Loose bound...}` to `\textbf{Loose bound...}` (paragraph styling was inconsistent with surrounding text) | `daml/sections/methods_rank.tex` |
| Ranking estimator justification moved | Moved the "why not use a TopKMask-based ranking estimator" justification from the supplementary into the main Methods Rank section | `daml/sections/methods_rank.tex`, `daml/supp_sections/supp_ranking.tex` |
