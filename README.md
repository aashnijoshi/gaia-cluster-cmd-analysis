# Gaia Cluster CMD Analysis: Hyades Membership & Isochrone Fitting

This project uses **Gaia DR3 astrometric and photometric data** to identify members of the **Hyades open cluster** and construct high-quality **color–magnitude diagrams (CMDs)**. The analysis demonstrates robust data filtering, multivariate clustering in phase space, and comparison to **theoretical stellar evolution models (MIST isochrones)**.

While motivated by an astrophysical application, the workflow mirrors common **data science tasks**: noisy real-world data ingestion, feature engineering, quality control, clustering, model comparison, and diagnostic visualization.

---

## Overview

The goals of this project are to:

- Query and cache large-scale observational data from a remote archive (Gaia)
- Clean and filter noisy measurements using domain-informed quality criteria
- Identify cluster members using **multidimensional feature space clustering**
- Construct and analyze empirical trends in the data (CMDs)
- Compare observations to theoretical models and evaluate best-fit parameters

The Hyades cluster is particularly well-suited for this analysis due to its proximity, rich Gaia coverage, and well-studied age and metallicity.

---

## Data Source

- **Gaia DR3** (`gaiadr3.gaia_source`)
- Accessed programmatically using `astroquery.gaia`
- Cached locally to ensure reproducibility and avoid repeated remote queries

Key features used:
- Astrometry: parallax, proper motions
- Photometry: G, BP, RP magnitudes
- Quality indicators: RUWE, visibility periods, flux-over-error ratios

---

## Methodology

### 1. Data Ingestion & Caching
- ADQL queries to the Gaia archive
- Results cached as FITS files to support reproducible analysis

### 2. Feature Engineering
- Absolute magnitude computed from parallax
- Color index constructed from Gaia BP–RP bands
- Signal-to-noise ratios derived for astrometric validation

### 3. Quality Filtering
Inspired by Gaia collaboration recommendations:
- Parallax SNR threshold
- Astrometric stability (RUWE)
- Photometric reliability and excess flux filtering

This step removes spurious measurements and blended sources.

### 4. Cluster Membership Selection
Instead of simple thresholding, cluster membership is determined using a **robust 3D selection in phase space**:
- Proper motion in RA
- Proper motion in Dec
- Parallax

A median-centered, MAD-scaled distance metric (Mahalanobis-style) is used to retain stars consistent with the cluster kinematics and distance.

### 5. Visualization
- Global color–magnitude diagram
- Diagnostic plots illustrating the effect of each selection step
- Zoomed-in views of the **main-sequence turnoff**, highlighting age sensitivity

### 6. Model Comparison
- MIST theoretical isochrones (Gaia EDR3 passbands)
- Comparison across a grid of ages and metallicities
- Best-fit parameters inferred from main-sequence alignment and turnoff morphology

---

## Key Results

- Clean Hyades CMD with a tight main sequence and visible binary sequence
- Clear separation between cluster members and field contamination
- Best-fit age consistent with literature values (~600–700 Myr)
- Metallicity trends consistent with a mildly super-solar population

---

## Why This Project

This project highlights skills relevant to **data science and applied ML roles**:

- Working with large, imperfect datasets
- Building reproducible data pipelines
- Multivariate clustering and robust statistics
- Model–data comparison and diagnostics
- Clear, interpretable visualizations
- Scientific reasoning grounded in quantitative evidence

Although the domain is astrophysics, the techniques generalize directly to problems in analytics, ML, and data-driven decision making.

---

## Tech Stack

- Python
- NumPy, Pandas
- Matplotlib
- Astropy / Astroquery
- Gaia Archive (ADQL)

---

## Future Extensions

- DBSCAN / Gaussian Mixture clustering in phase space
- Cross-validation of age/metallicity fits
- Extension to additional clusters (M67, NGC 6397)
- Automated membership classification pipeline

---

## Author

Aashni Joshi  
UC Berkeley  
Data Science & Physics  
