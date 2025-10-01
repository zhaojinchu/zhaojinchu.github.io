---
layout: page
title: Body Measurement Predictor
description: PyTorch regression model and Tkinter app forecasting physique changes after weight adjustments.
img: assets/img/body-measurement.png
importance: 1
category: work
related_publications: false
profile_date: 2023-03-02
profile_importance: 1
profile_summary: Engineered a preprocessing-to-inference pipeline that predicts measurement deltas and ships as a desktop app.
---

A machine learning playground that turned into a polished desktop tool: I built this pipeline to estimate how a client’s body measurements could shift after changing weight. From data prep to PyTorch training to a Tkinter GUI, it all lives here. Repo: [github.com/zhaojinchu/BodyMeasurementPredictor](https://github.com/zhaojinchu/BodyMeasurementPredictor).

**Product flow**
- Tkinter desktop app lets coaches plug in current stats, target weight, and instantly see projected measurement deltas.
- GUI constrains skeletal metrics (wrists, ankles, shoulder-to-crotch) so predictions stay realistic.
- Packaging checklist documents how to ship the tool with PyInstaller for offline use.

**Model pipeline**
- `preprocess.py` cleans and augments datasets, simulating multiple weight-change scenarios before scaling features.
- PyTorch regressors (`train2.py`, `train3.py`) train on percentage deltas with early-stop checkpoints and scaler persistence.
- Inference scripts reverse the scaling, clamp deltas, and output centimetre estimates that stay consistent across CLI and GUI.

**Tooling & ops**
- Saved scalers, model weights, and augmented CSVs live alongside code for reproducible retraining.
- Synthetic augmentation + StandardScaler combos cut down on overfitting and simplify iterative experiments.
- Troubleshooting docs cover data sanity checks and PyInstaller options for Windows environments.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/body-measurement.png" title="Body measurement predictor GUI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Placeholder – capture the Tkinter app with a sample prediction once you rebuild the executable.
</div>

Next up: add confidence intervals around each prediction and expand the dataset to support additional demographics.
