# Ruliological Resilience in Elementary Cellular Automata
### Quantifying Pattern Restoration Across Rule Space

---

## 🧠 Overview

This project provides a **quantitative framework for measuring recovery and robustness** in one-dimensional elementary cellular automata (ECA).

We investigate how computational systems respond to localized perturbations ("injuries") and whether they return to their original pattern-generating trajectory.

The central contribution is the definition and systematic evaluation of a **Restoration Coefficient (R)** across all 256 ECA rules.

---

## 🎯 Objectives

- Define a **reproducible metric of pattern restoration**
- Systematically evaluate all 256 ECA rules under perturbation
- Characterize recovery behavior across Wolfram classes
- Identify structural regimes of robustness and fragility

---

## 🔬 System Definition

We study elementary cellular automata defined by:

- Binary states: \( s_i \in \{0,1\} \)
- Lattice size: \( L \)
- Local update rule: \( r \in [0,255] \)

Initial condition:
- Single active cell centered in an otherwise zero state

Boundary conditions:
- Periodic (default)

---

## 🧪 Experimental Design

For each rule:

1. Generate a **control trajectory** \( C(t) \)
2. Introduce a localized perturbation at time \( t_p \)
3. Generate a **perturbed trajectory** \( I(t) \)
4. Compute divergence and recovery metrics

---

## ⚡ Perturbation Model

We define three perturbation ("injury") types:

- **RandomMix** — random bit replacement (noise injection)
- **Void** — zeroing a region (information removal)
- **BitFlip** — inversion of local bits

Perturbation parameters:
- Time of injury: \( t_p \)
- Width: \( W \)
- Location: centered

---

## 📊 Divergence Metric

We quantify deviation using normalized Hamming distance:

\[
D(t) = \frac{1}{L} \sum_{i=1}^{L} |C_i(t) - I_i(t)|
\]

---

## 📈 Restoration Metrics

### Restoration Coefficient

\[
R = 1 - \frac{1}{T} \sum_{t = t_p + 1}^{t_p + T} D(t)
\]

Interpretation:
- \( R = 1 \): perfect restoration
- \( R \approx 0 \): persistent divergence
- intermediate \( R \): partial recovery

---

### Additional Metrics

- **Final Restoration**
  \[
  R_{\text{final}} = 1 - D(t_{\text{final}})
  \]

- **Shift-Tolerant Restoration**
  Accounts for spatial displacement via optimal alignment

- **Restoration Time (\(\tau\))**
  Time to stable recovery below threshold \( \epsilon \)

---

## 🔁 Multi-Trial Protocol

Each rule is evaluated over multiple trials:

- Random perturbation realizations
- Aggregated statistics:
  - Mean \( R \)
  - Standard deviation
  - Mean restoration time

---

## 📊 Outputs

The pipeline generates:

- Scatter plots: \( R \) vs rule index  
- Histograms: distribution of \( R \)  
- Box plots: grouped by Wolfram class  
- Time-series: \( R(t) \) dynamics  
- Difference maps (XOR visualizations)

---

## 🧩 Key Findings

### 1. Structured Distribution of Restoration

Restoration is not uniform across rule space.

- **Class I / II** → high \( R \), rapid recovery  
- **Class III** → near-zero \( R \), irreversible divergence  
- **Class IV** → intermediate \( R \), localized recovery  

---

### 2. Three Regimes of Response

We identify three distinct dynamical regimes:

1. **Full Restoration**
   - Rapid convergence to control trajectory

2. **Partial / Structured Recovery**
   - Localized divergence ("scars")
   - Preservation of global structure

3. **Irreversible Divergence**
   - Expanding error cones
   - Loss of trajectory coherence

---

### 3. Phase-Dependent Recovery

For complex rules (e.g., Rule 110):

- Early perturbations → system-wide divergence  
- Late perturbations → localized recovery  

This indicates a **developmental or maturity-dependent stability regime**.

---

### 4. Critical Perturbation Thresholds

Recovery depends on perturbation scale:

- Small \( W \) → recovery  
- Large \( W \) → collapse  

Suggesting a **capacity limit for repair**.

---

### 5. Exact vs Functional Recovery

Some rules restore:
- **Exact state** (bitwise identical)

Others restore:
- **Functional structure** (with spatial displacement)

---

## ⚙️ Computational Parameters

Typical values:

- Lattice size: \( L = 200 \)
- Total steps: \( 300 \)
- Perturbation time: \( t_p = 50 \)
- Perturbation width: \( W = 20 \)
- Recovery window: \( T = 100 \)
- Trials per rule: \( n = 20–50 \)

---

## ▶️ Running the Code

Open:

```

notebooks/ruliology_histograms.nb

````

Run:

```wolfram
runRuleBatch[Range[0, 255], 50]
````

Outputs:

* CSV data (trial + summary)
* Figures for analysis

---

## 📁 File Structure

```
paper_1_eca_resilience/
│
├── notebooks/
│   ├── ruliology_histograms.nb
│   ├── test_1d_wolfram_rules.nb
│   └── testWolframsTopRules.nb
│
├── data/
├── figures/
└── README.md
```

---

## 🔭 Interpretation

This study reframes cellular automata as systems with:

> **measurable repair capacity**

rather than purely generative complexity.

---

## 📌 Conceptual Contributions

* Formal definition of **Restoration Coefficient (R)**
* Identification of **repair regimes in rule space**
* Quantitative framework for **post-perturbation dynamics**
* Distinction between **exact and functional recovery**

---

## 🚀 Next Steps

* Extend analysis to 2D systems (see Paper 2)
* Map full **complexity–repair phase space**
* Explore links to:

  * computational universality
  * biological regeneration
  * noise tolerance in complex systems

---

## 📜 Citation (Draft)

```id="eca_cite"
Ather, S. H., Gordon, R. (2026).
Ruliological Resilience: Pattern Restoration in Elementary Cellular Automata.
```

---

## 🧑‍💻 Authors

**Syed Hussain Ather**
Georgia Tech (OMSA)
AI Engineer — AAK Tele-Science

**Dr. Richard Gordon**

---

## ⚡ Summary

> Not all rules compute the same way.
> Some rules **recover**.

