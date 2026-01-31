# GeneCover

[![PyPI-Server](https://img.shields.io/pypi/v/genecover.svg)](https://pypi.org/project/genecover/)
[![Project generated with PyScaffold](https://img.shields.io/badge/-PyScaffold-005CA0?logo=pyscaffold)](https://pyscaffold.org/)

A combinatorial approach for **label-free marker gene selection** from scRNA-seq and spatial transcriptomics data, using gene–gene correlation and set cover.

This repository is a **Python packaging + PyPI-friendly** version of the original GeneCover pipeline, keeping the algorithm behavior as close as possible to the original implementation while supporting optional solver backends (uses lazy loading).

---

## Manuscript

Wang, A., Hicks, S., Geman, D., & Younes, L. (2025, April).  
*GeneCover: A Combinatorial Approach for Label-free Marker Gene Selection*.  
In International Conference on Research in Computational Molecular Biology (pp. 354–357). Cham: Springer Nature Switzerland.  
DOI: [10.1101/2024.10.30.621151](https://doi.org/10.1101/2024.10.30.621151)


```bibtex
@inproceedings{wang2025genecover,
  title={GeneCover: A Combinatorial Approach for Label-free Marker Gene Selection},
  author={Wang, An and Hicks, Stephanie and Geman, Donald and Younes, Laurent},
  booktitle={International Conference on Research in Computational Molecular Biology},
  pages={354--357},
  year={2025},
  organization={Springer}
}
```

Original resources:

- Original GitHub repo: https://github.com/ANWANGJHU/GeneCover  
- Original docs site: https://genecover.readthedocs.io/

---

## Features

- Compute gene–gene correlation matrices from scRNA-seq / spatial transcriptomics data:
  - Spearman correlation (default)
  - Pearson correlation
- Select marker genes via **minimal-weight set cover**, with multiple backends:
  - **Gurobi** (integer programming; requires license)
  - **SCIP** via PySCIPOpt (open-source solver)
  - **Greedy heuristic** (no solver dependencies; NumPy-only)
- Perform **iterative marker selection** (`Iterative_GeneCover`) to build gene panels in multiple rounds
- Behavior closely aligned with the original one-file GeneCover implementation

---

## Installation

### Install from PyPI (recommended)
```bash
pip install genecover
```

This installs the core package and supports the Greedy backend (no external solver required).

### Optional solver backends

To use integer-programming solvers, install extras:

# Gurobi backend (requires a valid Gurobi license)
pip install "genecover[gurobi]"

# SCIP backend (via PySCIPOpt)
pip install "genecover[scip]"

# Install all optional backends
pip install "genecover[all]"