# ERWS: Energy Restricted Workflow Scheduling in Heterogeneous Multiprocessor Systems

This repository contains the experimental results accompanying the paper:

> **ERWS: Energy Restricted Workflow Scheduling in Heterogeneous Multiprocessor Systems**  
> Wakar Ahmad, Lohith Silaparasetti, Priyanshu Arya, Sameer Pandya, Pradeep Kumar, Tayyab Khan, Abdulatif Alabdultif  
> *Under review*

---

## Contents

```
├── Strict/          # NSL plots for strict energy constraints (λ = 1.2 to 3.0, step 0.2)
│   ├── FFT.png
│   ├── GE.png
│   ├── Genome.png
│   ├── LA.png
│   ├── LIGO.png
│   └── Montage.png
│
├── Relaxed/         # NSL plots for relaxed energy constraints (λ = 1.4 to 3.0, step 0.4)
│   ├── FFT.png
│   ├── GE.png
│   ├── Genome.png
│   ├── LA.png
│   ├── LIGO.png
│   └── Montage.png
│
└── LICENSE
```

---

## Overview

ERWS is a three-phase energy-constrained workflow scheduling algorithm for DVFS-enabled heterogeneous multiprocessor systems. It minimizes makespan subject to a global energy constraint by:

1. **Task prioritisation** — ranking tasks using the HEFT upward-rank metric.
2. **Energy pre-assignment** — distributing slack energy among tasks in proportion to their Minimum Energy Contribution Level (MECL) coefficient.
3. **Processor–frequency selection** — selecting the processor–frequency pair that minimises the earliest finish time within each task's pre-assigned energy limit.

---

## Workflows

Results are reported on six real-world scientific workflows commonly used in the scheduling literature:

| Workflow | Description |
|----------|-------------|
| **FFT** | Fast Fourier Transform — recursive spectral transform |
| **GE** | Gaussian Elimination — matrix factorization for solving linear equations |
| **Genome** | DNA sequence analysis pipeline |
| **LA** | Linear Algebra — matrix and vector operation kernels |
| **LIGO** | Gravitational-wave signal processing |
| **Montage** | Astronomical image mosaicking |

---

## Baseline Algorithms

ERWS is compared against five state-of-the-art energy-constrained workflow scheduling algorithms:

| Algorithm | Allocation strategy |
|-----------|---------------------|
| **MSLECC** | Dynamic greedy reclamation at runtime |
| **ESECC** | Equal slack distribution across all tasks |
| **ISAECC** | Weight-based allocation proportional to average energy |
| **REP** | Elasticity-based allocation proportional to energy range |
| **RSMECC** | Global scaling ratio applied uniformly to all tasks |

---

## Experimental Setup

- **Energy constraint:** $E_{\text{given}}(G) = \lambda\ \times E_{\min}(G)$
- **Strict regime:** $\lambda \in \{1.2, 1.4, 1.6, 1.8, 2.0, 2.2, 2.4, 2.6, 2.8, 3.0\}$
- **Relaxed regime:** $\lambda \in \{1.4, 1.8, 2.2, 2.6, 3.0\}$
- **Performance metric:** Normalized Schedule Length (NSL) — makespan of the evaluated algorithm normalised by the makespan of energy-unconstrained HEFT
- **Platform:** Apple MacBook Air M2, 8-core, 16 GB RAM

---

## Key Results

At the tightest strict budget ($\lambda = 1.4$), ERWS reduces NSL relative to MSLECC by **37–41%** across all six workflows (average **39.3%**), and achieves average gains of **7.5%** over ESECC, **8.6%** over RSMECC, **5.8%** over ISAECC, and **5.4%** over REP.

At $\lambda = 2.2$ (relaxed regime), the average improvement over MSLECC increases to **44.4%**, while gains over the static baselines remain in the range of **5–7%** on average.

---

## Citation

If you use these results in your work, please cite:

```bibtex
@misc{ahmad2025erws,
  author       = {Ahmad, Wakar and Silaparasetti, Lohith and Arya, Priyanshu
                  and Pandya, Sameer and Kumar, Pradeep and Khan, Tayyab
                  and Alabdultif, Abdulatif},
  title        = {{ERWS}: Energy Restricted Workflow Scheduling in
                  Heterogeneous Multiprocessor Systems -- Experimental Results},
  year         = {2025},
  howpublished = {\url{https://github.com/Gitsike/ERWS-Energy-Restricted-Workflow-Scheduling-in-Heterogeneous-Multiprocessor-Systems}},
  note         = {Accessed: \today}
}
```

---

## License

This repository is licensed under the [Apache License 2.0](LICENSE).
