# Branches

`main` is strictly behind both feature branches — each branch contains
all of `main` plus its own top-K work and DAML clarifier. Don't commit
new shared work to `main` without rebasing the branches afterward.

## `main`
Shared committee-feedback fixes for ch5:
- Non-convexity / initialization note in `sec_methods.tex`
- Portfolio surrogate-method caveat in `sec_methods.tex` and `sec_expt_bench.tex`

## `topk-drop`
Removes the real-world top-K section (`sec_expt_topK.tex`), its appendix
(`app_topK.tex`), the 6-panel figure include, and the three
`hyperplane_landscape_*.pdf` figures. References cleaned in
`sec_intro.tex`, `sec_conclusion.tex`, `supplementary/ch5_dpo.tex`. DAML
chapter has a clarifier on PG/SPO+ training signal (no forward pointer).

## `topk-reframe`
Keeps the section, rewrites it around training-objective alignment
(BPR vs. unnormalized decision loss). Updated 5-panel figure caption
(BPR, SPO+ on decision loss, SPO+ on BPR, PG on decision loss, PG on BPR).
Adds `app_bpr_setup.tex` with oracle problem + predicted quantities
drawn from \citet{heuton2025decisionaware}. DAML chapter clarifier
includes a forward pointer to ch5 Fig.~\ref{fig:topK_interpolation_main}.

## Pick a winner
Build PDFs are at `thesis_main.pdf` on each branch (also copied to
`~/Downloads/thesis_main_{drop,reframe}.pdf`). Once you pick, fast-forward
or merge the chosen branch into `main`.
