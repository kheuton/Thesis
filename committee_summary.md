
### 1. Formal definition of decision problems (Chapter 5, PnO Benchmarks)
Added a new table in the PnO Benchmark Replication section that formally specifies, for every experiment, the prediction $\hat y$, decision space $\mathcal{Z}$, objective, constraints, and dataset sizes. 

### 2. Surrogate usage and hyperparameter specification (Chapter 5)
- Added a table listing each method's tunable hyperparameter, validation grid, and shared training settings.
- Added a head-to-head comparison of fixed vs. validation-tuned hyperparameters: a per-method mean improvement summary in the main text, with the full per-task breakdown in the appendix 

### 3. Overfitting diagnostics (Chapter 5 appendix)
Added seven per-task tables reporting training, validation, and test prediction loss alongside decision regret for every method. 

### 4. Loss-landscape visualization (Chapter 5, Real-world Top-K Selection section and appendix)
Replaced the 1D linear-interpolation figure with a 2D hyperplane landscape parameterized as $\theta(s,t) = (1-s-t)\theta_{DPO} + s\,\theta_{PG} + t\,\theta_{SPO^+}$. The new figure addresses several feedback items at once:
- The sweep is extended beyond $[0,1]$ in both $s$ and $t$ to expose the broader landscape.
- Per-task footers report the hyperparameters used ($\sigma$, $h$, step sizes).
- Scales are comparable within each of four loss panels (BPR, NLL, SPO+, PG) 
- Cook County is shown in the main text; MA and Aerial Survey appear in the appendix.

### 5. Well-specified vs. misspecified framing (Chapter 5, Introduction and Benchmark Replication sections)
- Restructured the benchmark section into three regimes: Well-Specified, Misspecified, and Continuous and Gradient-Informative.
- Added a framing paragraph in the introduction citing Hu, Kallus, and Mao (2022) and Elmachtoub et al. (2025) to explain the strong performance of two-stage MSE on benchmark tasks.
- Added a tempering caveat in the benchmark section and a companion parenthetical in the conclusions noting that grid-searching $(\eta, b)$ on validation regret makes the nominally "decision-unaware" two-stage MSE baseline a coarse decision-aware method.

## Editorial and bibliographic cleanup

### Framing refinements throughout the front matter
- Softened the abstract's misalignment claim with the qualifier "when the model is misspecified or data is insufficient."
- Reworded the introduction's description of training to clarify which error is minimized on training data versus held-out data.
- Added the same "when the model is misspecified" qualifier to the misalignment claim in the introduction.
- Updated the introduction's chapter overview to highlight publication venues

### References
- Standardized citation formatting throughout Chapter 3: added missing whitespace before in-line citations and moved citations from after sentence-ending periods to before them.
- Consolidated duplicate entries

### Structural and presentation changes
- Translated BPR improvements into concrete real-world counts in the DAML results
- Moved the justification for not using a TopKMask-based ranking estimator from the DAML supplementary into the main Methods for Ranking section.
- Removed the inconsistent and undocumented cell highlighting from Tables 1 and 2 in Chapter 3
- Added PG to the benchmark rerun in Chapter 5
- Github links now consistently in front of chapter
