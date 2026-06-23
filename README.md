# Optical Modeling and Optimization of Perovskite Solar Cells

This repository contains our Design Credit Course project on **Transfer Matrix Method (TMM)-based optical modeling of a perovskite solar cell**. The project focuses on understanding light propagation, absorption, reflection, and optical losses in multilayer photovoltaic structures using physics-based simulation techniques.

The repository includes the complete project report, presentation slides, Google Colab notebook implementation, cleaned optical constants dataset, and generated simulation results.

---

## Repository Contents

```text
.
├── README.md
├── Project_Presentation.pptx
├── Project_Report.pdf
├── Transfer_Matrix_Method_(TMM).ipynb
├── cleaned_estimated_optical_constants.csv
└── tmm_absorption_results.csv
```

### Included Files

* **Project Presentation** – Summary of project objectives, methodology, and results.
* **Project Report** – Detailed technical report describing the modeling approach and findings.
* **Google Colab Notebook** – Complete implementation of the Transfer Matrix Method simulation workflow.
* **Cleaned Optical Constants Dataset** – Processed optical data prepared from SCAPS-1D output.
* **TMM Results File** – Generated absorption and optical simulation results.

---

# Project Overview

Perovskite solar cells have emerged as one of the most promising next-generation photovoltaic technologies due to their high efficiency and low fabrication cost. The optical performance of these devices depends strongly on how incident light interacts with the multilayer structure of the solar cell.

In this project, we implemented the **Transfer Matrix Method (TMM)** in Python to model the optical behavior of a perovskite solar-cell stack and estimate:

* Reflectance
* Layer-wise absorption
* Optical electric-field distribution
* Parasitic optical losses
* Maximum theoretical photocurrent density

The simulation enables analysis of photon management within the device and helps identify optical limitations before fabrication.

---

# Research Paper Reference

The methodology used in this project is based on the following research paper:

**TMM-Sim: A versatile tool for optical simulation of thin-film solar cells**

Leandro Benatto, Omar Mesquita, Kaike R. M. Pacheco, Lucimara S. Roman, Marlus Koehler, Rodrigo B. Capaz, Graziâni Candiotto

*Computer Physics Communications, Volume 300, 2024, 109206*

DOI: https://doi.org/10.1016/j.cpc.2024.109206

Journal Article:
https://www.sciencedirect.com/science/article/pii/S0010465524001292

---

# Device Structure

The optical model simulates a multilayer perovskite solar-cell architecture consisting of:

**Air / FTO / ETL / Perovskite / HTL / Metal**

The layer thicknesses used in the simulation are:

| Layer      | Thickness |
| ---------- | --------- |
| FTO        | 200 nm    |
| ETL        | 20 nm     |
| Perovskite | 1200 nm   |
| HTL        | 20 nm     |

The perovskite layer acts as the primary light absorber, while the remaining layers influence reflection, transmission, and parasitic absorption.

---

# Data Preparation

The project began with optical data obtained from **SCAPS-1D** simulations. The raw data was not directly suitable for Transfer Matrix Method calculations and therefore required preprocessing.

The dataset was cleaned and transformed into wavelength-dependent optical constants that could be used directly within the TMM framework.

The processed dataset contains:

* Wavelength values
* Refractive index (n)
* Extinction coefficient (k)
* Absorption-related parameters

These quantities are required to construct the complex refractive index:

N(λ) = n(λ) + i·k(λ)

which forms the basis of TMM calculations.

---

# Methodology

## 1. Transfer Matrix Method (TMM)

The Transfer Matrix Method is a widely used optical modeling technique for multilayer thin-film structures.

For each wavelength, the method calculates:

* Reflection
* Transmission
* Absorption
* Internal electric-field distribution

by solving electromagnetic wave propagation across multiple interfaces.

The simulation stack used in the notebook is:

```python
d_list = [np.inf, 200, 20, 1200, 20, np.inf]
```

corresponding to:

Air → FTO → ETL → Perovskite → HTL → Metal

---

## 2. Optical Absorption Analysis

The wavelength-dependent absorption profile is computed for each layer.

The active perovskite layer absorption is integrated with the AM1.5G solar spectrum to estimate the maximum achievable photocurrent.

Additional calculations quantify optical losses due to:

* Reflection
* FTO absorption
* ETL absorption
* HTL absorption
* Metal absorption

---

## 3. Electric Field Distribution

The notebook also calculates the depth-dependent electric-field intensity:

|E(x)|²

at selected wavelengths.

This analysis helps identify regions where optical energy is concentrated and evaluates how efficiently light is confined within the absorber layer.

---

# Results

The simulation demonstrates strong optical absorption within the perovskite layer and highlights the dominant optical loss mechanisms.

### Key Findings

* Perovskite is the dominant absorbing layer.
* Reflection represents the largest optical loss.
* Electric-field intensity is concentrated inside the absorber region.
* The modeled structure achieves high theoretical photocurrent generation.

### Numerical Results

| Parameter                               | Value        |
| --------------------------------------- | ------------ |
| Maximum Theoretical Photocurrent (Jmax) | 41.22 mA/cm² |
| Reflection Loss                         | 4.75 mA/cm²  |
| FTO Loss                                | 0.61 mA/cm²  |
| ETL Loss                                | 0.10 mA/cm²  |
| HTL Loss                                | 0.00 mA/cm²  |
| Metal Loss                              | 0.01 mA/cm²  |

The results indicate that reducing front-surface reflection would provide the greatest opportunity for further optical improvement.

---

# How to Run

## Requirements

Install the following Python packages:

```bash
pip install numpy pandas matplotlib scipy tmm
```

## Running the Notebook

1. Open the notebook in Google Colab or Jupyter Notebook.
2. Upload the cleaned optical constants dataset.
3. Run all notebook cells sequentially.
4. Generate the absorption and photocurrent calculations.

---

# Generated Outputs

The notebook produces:

* Layer-wise absorption spectra
* Reflectance spectrum
* Electric-field distribution plots
* Photocurrent calculations
* Optical loss analysis
* TMM absorption results table

The primary numerical output is stored in:

```text
tmm_absorption_results.csv
```

---

# Educational Significance

This project demonstrates how computational optical modeling can be used to analyze and optimize photovoltaic devices before fabrication.

By applying the Transfer Matrix Method, it becomes possible to:

* Predict optical performance
* Quantify loss mechanisms
* Optimize layer thicknesses
* Estimate theoretical current generation
* Guide future solar-cell design decisions

The workflow presented in this repository can serve as a foundation for further research involving electrical simulation, device optimization, and advanced photovoltaic modeling.

---

# Citation

If you use this repository or build upon this work, please cite the original paper:

```bibtex
@article{benatto2024tmmsim,
  title={TMM-Sim: A versatile tool for optical simulation of thin-film solar cells},
  author={Benatto, Leandro and Mesquita, Omar and Pacheco, Kaike R. M. and Roman, Lucimara S. and Koehler, Marlus and Capaz, Rodrigo B. and Candiotto, Graziâni},
  journal={Computer Physics Communications},
  volume={300},
  pages={109206},
  year={2024},
  doi={10.1016/j.cpc.2024.109206}
}
```

---

# Acknowledgements

This work was completed as part of a Design Credit Course project. We acknowledge the guidance and support provided throughout the course and the contributions of the authors of the original TMM-Sim research paper, whose methodology formed the foundation of this project.
