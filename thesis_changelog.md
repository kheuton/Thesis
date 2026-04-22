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

### 4d. (Optional / stretch) Combined visualization
- [ ] Consider replacing the two 1D plots with a single 2D visualization: the **hyperplane formed by the affine combination of $\theta_{PG}$, $\theta_{DPO}$, and $\theta_{SPO+}$**, showing decision loss (and/or surrogate loss) as a surface or heatmap over that plane.

---

## Change log

| Item | Change | Location in thesis |
|------|--------|--------------------|
|      |        |                    |
