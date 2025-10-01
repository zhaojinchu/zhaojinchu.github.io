---
layout: page
title: Vanilla License Plate CNN
description: Research sandbox for lightweight PyTorch detectors localizing license plates with custom data tooling.
img: assets/img/vanilla-lpr.png
importance: 1
category: work
related_publications: false
profile_date: 2025-10-1
profile_importance: 1
profile_summary: Prototyped CNN-based license plate localization with a bespoke preprocessing pipeline and mixed-precision training loops.
---

This repo is where I iterated on compact CNNs for license plate localisation—building the preprocessing, training, and evaluation stack from scratch in PyTorch. It let me benchmark ResNet, MobileNetV3, EfficientNet, and my own depthwise network on unified datasets I curated. Repo here: [github.com/zhaojinchu/vanilla_LPR_CNN](https://github.com/zhaojinchu/vanilla_LPR_CNN).

**Experiment goals**
- Treat plate localisation as a single-object regression problem with `(x_min, y_min, x_max, y_max)` outputs.
- Compare backbone trade-offs (accuracy vs. params vs. throughput) across ResNet, MobileNet, EfficientNet, and custom CNNs.
- Stress-test mixed-precision training to keep GPU utilisation high while experimenting on laptops and lab machines.

**Model tooling**
- Configurable training scripts (`train.py`, `test_train.py`, `test_train2.py`) that resume from checkpoints and log IoU/F1 to CSV.
- Factory-driven `MODEL_MAP` makes swapping backbones a one-line change while keeping a shared regression head.
- Automatic checkpoint rotation that snapshots `best_model_epoch_*.pth` and captures hyperparameters alongside metrics.

**Data & evaluation**
- Preprocessing pipeline merges CCPD2019 and Kaggle YOLO datasets, letterboxes imagery, and normalises annotations.
- Iterable dataset streams samples from CSV, applies augmentations, and feeds 640×480 tensors to the trainers.
- Evaluation scripts surface IoU, precision/recall, FPS, and model size to contextualise each experiment.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/vanilla-lpr.png" title="License plate localisation experiments" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Placeholder – drop in a training metrics chart or qualitative detection sample.
</div>

Next up: port the best-performing backbone into a multi-object detector and bolt on OCR so it can run alongside the YOLO pipeline.
