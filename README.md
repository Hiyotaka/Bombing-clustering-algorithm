# Bombing Clustering Algorithm

Publication-oriented repository for the Bombing clustering method, with reproducible MATLAB code and manuscript-ready writing assets.

## Abstract
Bombing is a density-based clustering method that integrates joint k-nearest neighbor graph (jNNG), Gaussian kernel density correction, local neighbor density, and BFS-based region expansion. The method supports both known-K clustering and automatic K discovery, and is designed to be robust to irregular shapes, overlap, and noise.

## Contributions
- jNNG-based global density estimation using geodesic distance.
- Two-round sigmoid correction for global density calibration.
- Dynamic-radius local density and mixture density fusion.
- BFS-driven generalized cluster discovery (reachable region + boundary region).
- Degree-of-adjacency criterion for deciding split vs merge under unknown K.

## Repository Structure
```text
.
|- Bombing.m                       # Main MATLAB class
|- data_set/                       # Synthetic and real datasets
|  |- two_dim/
|  |- real/
|- index/                          # Evaluation indices (NMI/FMI/ARI/AMI)
|- graph/                          # Graph utilities
|- supplementary.pdf               # Supplementary material
|- bombing.pdf                     # Published paper PDF
`- paper/
   |- MANUSCRIPT_TOP_TIER.md       # Top-tier manuscript draft template
   `- FIGURE_INSERTION_MAP.md      # Figure-number insertion map
```

## Quick Start (MATLAB)
```matlab
load('data_set/two_dim/DS1.mat');   % variable: data
bo = Bombing(data);
idx = bo.find_cluster(0);            % K <= 0: auto-detect K
% idx = bo.find_cluster(K);          % known-K mode
```

## Reproducibility Notes
- Input data are normalized in `Bombing.m` before clustering.
- Default key hyperparameters are configured in the class properties:
  - `dc = 0.1`
  - `reach_index = 0.6`
  - `tocluster_index = 5`
- For unknown-K mode, call `find_cluster(0)` (or any `K <= 0`).


## Citation
Use the following BibTeX entries:

@article{fei2025bombing,
  title   = {Discovering generalized clusters with adaptive mixture density-based clustering},
  author  = {Fei, Zexuan and Zhai, Haoyu and Yang, Jie and Wang, Bin and Ma, Yan},
  journal = {Knowledge-Based Systems},
  volume  = {314},
  pages   = {113250},
  year    = {2025},
  doi     = {10.1016/j.knosys.2025.113250},
  url     = {https://doi.org/10.1016/j.knosys.2025.113250}
}


The same entries are also saved in `paper/references.bib`.
