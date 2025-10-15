---
layout: page
title: YOLOv5 License Plate Recognition
description: End-to-end license plate detection and OCR pipeline powered by YOLOv5 and Fast Plate OCR.
img: assets/img/7.png
importance: 1
category: work
related_publications: false
profile_date: 2025-01-27
profile_importance: 1
profile_summary: Combined a custom YOLOv5 detector with histogram-boosted preprocessing and ONNX OCR to read plates end-to-end.
---

This project stitches detection, pre-processing, and OCR into a single script that reads license plates from noisy street captures. I fine-tuned YOLOv5 on a Kaggle dataset, layered in histogram/threshold filters, and integrated Fast Plate OCR to land text predictions with high recall. Repo here: [github.com/zhaojinchu/YolovLicensePlateRecognition](https://github.com/zhaojinchu/YolovLicensePlateRecognition).

**Pipeline overview**
- YOLOv5 detector localises plates, with weights saved under `outputs/train/license_detection2/weights/best.pt`.
- Contrast-limited adaptive histogram equalisation plus adaptive thresholding stabilise plates before OCR.
- Fast Plate OCR (ONNX) decodes characters and feeds annotated outputs back into the final imagery.

**Training setup**
- Wrapped Ultralytics’ training loop with `train_yolov.py` so I can re-run experiments with new datasets or hyperparameters.
- Dataset YAML + preprocessed YOLO splits ship in-repo, making it easy to swap in custom data.
- GPU-friendly requirements lock to Python 3.12.7 + CUDA 12.4 wheels, with CPU fallbacks when needed.

**Deployment notes**
- Inference script batches through `preprocessed_dataset/images/test`, saving annotated results and streaming predictions to stdout.
- Config flags expose detection confidence, weight paths, and output directories for quick experimentation.
- Packaging advice covers ONNX/OpenCV dependencies so the pipeline stays portable across dev machines.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/yolov-license-plate.png" title="YOLOv5 + OCR pipeline" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Placeholder
</div>

Next up: wire the detector into a live video stream and benchmark latency with TensorRT for real-time edge deployments.
