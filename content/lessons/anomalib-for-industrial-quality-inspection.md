+++
title = "Anomalib for industrial quality inspection"
description = "Short tutorial on building a visual quality inspection pipeline with fewer labelled defect examples, using Anomalib's ready-made anomaly detection models and the MVTec AD 2 benchmark dataset."

[taxonomies]
skill = ["ai", "machine_learning", "materials_science"]
difficulty = ["intermediate"]
maturity = ["stable"]

[extra]
tags = ["short-tutorial", "anomaly-detection", "anomalib", "mvtec-ad2", "manufacturing", "pytorch", "quality-inspection"]
external_url = "https://swedenaifactory.se/short-tutorials/2026/06/anomalib-for-industrial-quality-inspection/"
+++

## Overview

This short tutorial shows how to build a visual quality inspection pipeline when labelled defect examples are scarce. Instead of training a classifier on many examples per defect class, you train on mostly-normal images and flag deviations, using Anomalib's ready-made datamodules, model integrations, and evaluation utilities, with a full walkthrough training PatchCore on the MVTec AD 2 `sheet_metal` dataset.

## Key takeaways

- Why anomaly detection fits sparse-label manufacturing data: train on normal images and flag deviations instead of requiring many labelled examples per defect class
- How Anomalib removes boilerplate: swap architectures without rewriting the training loop, thanks to ready-made datamodules, model integrations, and evaluation utilities
- How to train PatchCore, a strong industrial baseline based on a memory bank of pretrained backbone features, on MVTec AD 2 `sheet_metal`
- How to evaluate on the MVTec AD 2 test split to measure detection and localisation before adapting to your own cameras and parts
- How to adapt the pipeline to company data: keep the imaging setup stable, mirror the normal/abnormal folder layout, then sweep model and backbone choices

## Who is this for?

- Engineers and practitioners working on visual inspection in manufacturing and industrial settings
- Data scientists and ML practitioners looking for a practical anomaly detection workflow with public data

## Prerequisites

- Basic Python programming skills
- Familiarity with PyTorch fundamentals
- GPU access recommended for training
