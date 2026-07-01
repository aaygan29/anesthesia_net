# AnesthesiaNet: LLM Suppression as a Proxy for Consciousness Depth

AnesthesiaNet is an *in silico* mechanistic interpretability and computational neuroscience framework. The goal of this repository is to investigate whether structural and algorithmic constraints in large language models (LLMs) can serve as mathematical proxies for pharmacological neural inhibition in humans.

By treating targeted structural interventions—such as attention dropout scaling and token-entropy injection—as an artificial "anesthetic titration dial," we systematically disrupt a transformer network’s capacity for long-range integration. We extract the model's internal activation tensors under varying degrees of suppression, compute high-dimensional complexity metrics, and validate the resulting metrics against open-source human neuroimaging data during the descent into anesthesia.

---

## Research Questions

### Primary Research Question

* **Can artificial suppression parameters in transformer architectures (attention dropout and token-level noise) simulate a reliable, predictable mathematical analog to biological neural inhibition (propofol-induced human anesthesia)?**

### Secondary Research Questions

1. **Representational Collapse:** Which specific hidden layers or internal attention heads are most vulnerable to structural de-integration, and where does the network's effective rank contract first?
2. **Cross-Domain Alignment:** How strongly do spatial information metrics like Von Neumann Entropy ($VNE$) across deep activation layers correlate with temporal Lempel-Ziv complexity ($LZc$) drops captured from human EEG data?
3. **Monotonicity Boundaries:** Does an artificial suppression dial scale monotonically across an array of open-source models, or do specific foundation architectures possess structural resilience to simulated sedation?

---

## 🛠️ Project Proceeding Outline

This project is built as a modular, 4-phase pipeline designed for a rapid 6-to-8 week execution cycle.

```
├── data/              # Human baseline EEG data and text corpora
├── src/
│   ├── baseline/      # Human data preprocessing and LZc calculation
│   ├── model_dial/    # PyTorch hooks for attention-dropout and layer injection
│   └── analysis/      # VNE metrics and Isotonic regression alignment
└── notebooks/         # Calibration curve generation and testing

```

### Phase 1: Human Baseline Pipeline & Feature Preparation

* [ ] Download the open-source **`ds003171`** dataset (simultaneous EEG-fMRI during graded propofol-induced sedation).
* [ ] Preprocess high-density EEG time-series and binarize state arrays around the signal median.
* [ ] Calculate baseline empirical Lempel-Ziv Complexity ($LZc$) arrays mapping the clinical continuum: `Wakeful -> Sedated -> Unconscious -> Recovery`.
* [ ] Curate a control text validation corpus (e.g., standard Wikipedia evaluation subset) for LLM evaluation.

### Phase 2: Building the LLM "Anesthetic Titration" Dial

* [ ] Set up an open-source model inference script using Hugging Face transformers (e.g., Llama-3-8B).
* [ ] Write custom PyTorch forward hooks to dynamically intercept hidden state activation tensors ($A \in \mathbb{R}^{B \times T \times D}$) layer-by-layer.
* [ ] Implement the continuous parameter suppression dial:
* **Variable $\alpha$:** Scalable multi-head attention dropout (from `0.0` to `0.8`).
* **Variable $\sigma$:** Layer-wise Gaussian noise injection to simulate generalized synaptic inhibition.



### Phase 3: Hidden State Metric Computation

* [ ] Execute baseline and suppressed inference sweeps across 20 uniform increments of the titration dial.
* [ ] Construct spatial covariance matrices ($\rho$) from hidden state outputs across every individual layer.
* [ ] Calculate the Von Neumann Entropy ($VNE$) of each density matrix by deriving its eigenvalue spectrum: $S(\rho) = -\sum \lambda_i \log \lambda_i$.
* [ ] Graph the layer-depth versus entropy-decay curves to identify the localized "workspace collapse" threshold.

### Phase 4: Monotone Regression & Statistical Alignment

* [ ] Construct a feature dataframe pairing the artificial suppression inputs with their corresponding activation entropy outputs.
* [ ] Deploy an Isotonic (Monotone) Regression model to project the multidimensional LLM suppression vectors onto the discrete clinical sedation levels from Phase 1.
* [ ] Compute Spearman rank correlation coefficients ($\rho_s$) to statistically evaluate alignment fidelity.
* [ ] Package the analytics code into a clean command-line tool and export calibration dashboards for target publication venues.
