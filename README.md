# youtube-contagion-modelling
> Applying epidemiological SIR/SEIR models to YouTube comment sentiment to quantify emotion contagion during crypto-financial crises.

## Abstract

Emotion spreads through online communities in ways that mirror infectious disease dynamics, yet the parameters and rates of this contagion remain poorly understood. This repository applies classical SIR, SEIR, SIRS, and SEIRS ordinary differential equation models to YouTube comment sentiment data across three cryptocurrency crisis events (FTX collapse, Crypto crash, Binance), fitting contagion parameters via Levenberg-Marquardt optimisation to characterise meso- and macro-level emotional dynamics. The work provides the first empirical parameter estimates for emotion contagion on YouTube, establishing that fear spreads faster than other emotions during financial crises.

## Research Context

- **Thesis:** *Epidemiology of Online Emotions* (Kok-Shun, 2026)
- **Chapter:** Chapter 4 — Emotional Dynamics in Online Communities
- **Contribution type:** Artefact (contagion modelling pipeline) + Theoretical (epidemiological framing of online emotion)
- **Associated papers:** "Can AI Learn to Surf the Wave of Emotions? Modelling Self-Organising Social Media Communities in Financial Crises," ACIS 2023; "Epidemiology of Online Emotions: Emotion Detection and Contagion Modelling of the FTX Collapse," PACIS 2024

## Methods

- SIR (Susceptible–Infected–Recovered) model
- SEIR (+ Exposed compartment)
- SIRS (+ Reinfection)
- SEIRS (+ Exposed + Reinfection)
- Parameter fitting via lmfit (Levenberg-Marquardt algorithm)
- spaCy NLP for text preprocessing
- Meso- and macro-level contagion analysis

## Datasets

| Dataset | Description | Access |
|---------|-------------|--------|
| FTX Crisis Comments | YouTube comment threads during FTX collapse (30 JSON files) | Collected |
| Crypto Crash Comments | YouTube comments during 2022 crypto crash (8 JSON files) | Collected |
| Binance Comments | YouTube comments during Binance crisis (10 JSON files) | Collected |
| Coinbase Comments | YouTube comments from Coinbase-related videos (17 JSON files) | Collected |

## Repository Structure

```
youtube-contagion-modelling/
├── ftx/                              # FTX collapse comment data (JSON)
├── crypto/                           # 2022 crypto crash comment data (JSON)
├── binance/                          # Binance crisis comment data (JSON)
├── coinbase/                         # Coinbase comment data (JSON)
├── archive/                          # Archived analysis files
├── out/                              # Model output figures
├── ContagionModels_FTX_SIR.ipynb
├── ContagionModels_FTX_SIR_I1_inf.ipynb
├── ContagionModels_FTX_SEIR.ipynb
├── ContagionModels_FTX_SEIR_I1_inf.ipynb
├── ContagionModels_FTX_SIRS.ipynb
├── ContagionModels_FTX_SIRS_I1_inf.ipynb
├── ContagionModels_FTX_SEIRS.ipynb
├── ContagionModels_FTX_SEIRS_I1_inf.ipynb
├── ContagionModels_FTX_Visualisation.ipynb
├── Contagion_Meso_Macro_Visualisation.ipynb
├── ContagionModels_Utils.ipynb
├── Parameters.xlsx                   # Fitted model parameters across all events
└── pyproject.toml
```

## Requirements & Setup

**Stack:** Python 3.13+, uv package manager, numpy, scipy, lmfit, tellurium, spaCy.

```bash
pip install uv
uv sync
python -m spacy download en_core_web_sm
```

## Usage

Run analysis notebooks for each crisis event and model variant. Fitted parameters are tracked in `Parameters.xlsx`. Adjust ODE initial conditions and run the Levenberg-Marquardt fitting for each dataset:

```
ContagionModels_FTX_SIR*   → SIR model fitting (standard and I1-initialised)
ContagionModels_FTX_SEIR*  → SEIR model fitting
ContagionModels_FTX_SIRS*  → SIRS model fitting (with reinfection)
ContagionModels_FTX_SEIRS* → SEIRS model fitting
ContagionModels_FTX_Visualisation          → FTX results visualisation
Contagion_Meso_Macro_Visualisation         → cross-event meso/macro analysis
ContagionModels_Utils                      → shared utility functions
```

## References

[1] B. V. Kok-Shun, J. Chan, G. Peko, and D. Sundaram, "Can AI Learn to Surf the Wave of Emotions? Modelling Self-Organising Social Media Communities in Financial Crises," in *ACIS 2023 Proceedings*, vol. 79, 2023.

[2] B. V. Kok-Shun, J. Chan, G. Peko, and D. Sundaram, "Epidemiology of Online Emotions: Emotion Detection and Contagion Modelling of the FTX Collapse," in *PACIS 2024 Proceedings*, vol. 1, 2024.

<details>
<summary>BibTeX</summary>

```bibtex
@inproceedings{P1_kok-shun_can_2023,
  title     = {Can {AI} {Learn} to {Surf} the {Wave} of {Emotions}? {Modelling} {Self}-{Organising} {Social} {Media} {Communities} in {Financial} {Crises}},
  volume    = {79},
  booktitle = {{ACIS} 2023 {Proceedings}},
  author    = {Kok-Shun, Brice Valentin and Chan, Johnny and Peko, Gabrielle and Sundaram, David},
  year      = {2023},
}

@inproceedings{P2_kok-shun_epidemiology_2024,
  title     = {Epidemiology of {Online} {Emotions}: {Emotion} {Detection} and {Contagion} {Modelling} of the {FTX} {Collapse}},
  volume    = {1},
  booktitle = {{PACIS} 2024 {Proceedings}},
  author    = {Kok-Shun, Brice Valentin and Chan, Johnny and Peko, Gabrielle and Sundaram, David},
  year      = {2024},
}
```

</details>
