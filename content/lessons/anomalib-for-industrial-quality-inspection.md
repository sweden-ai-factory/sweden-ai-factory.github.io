+++
title = "Anomalib for industrial quality inspection"
description = "Short tutorial on building an anomaly-detection quality inspection pipeline that works with few defect examples, using Anomalib and the MVTec AD 2 benchmark dataset."

[taxonomies]
skill = ["ai", "machine_learning", "materials_science"]
difficulty = ["intermediate"]
maturity = ["stable"]

[extra]
tags = ["short-tutorial", "anomaly-detection", "anomalib", "mvtec-ad2", "manufacturing", "pytorch", "quality-inspection"]
external_url = "https://swedenaifactory.se/short-tutorials/2026/06/anomalib-for-industrial-quality-inspection/"
+++

## Overview

This short tutorial shows how to build a visual quality inspection pipeline when
labelled defect examples are scarce. Instead of training a classifier on many
examples per defect class, you train on normal images only and flag deviations,
using Anomalib's ready-made datamodules, model integrations, and evaluation
utilities, with a full walkthrough training PatchCore on the MVTec AD 2
`sheet_metal` dataset.

## Key takeaways

- Explain why anomaly detection suits industrial inspection data where normal
  images are plentiful but labelled defects are scarce: learn what "good" looks
  like and flag deviations, instead of collecting many labelled examples per
  defect class
- Use Anomalib's ready-made datamodules, model classes, and Engine (built on
  PyTorch Lightning) to assemble the pipeline from data loading through
  evaluation, swapping the model or its backbone without changing the training
  code
- Train PatchCore — an industrial baseline that builds a memory bank of patch
  features from a pretrained backbone (ResNet50 by default) and scores test
  patches against it — on the MVTec AD 2 `sheet_metal` category
- Inspect anomaly maps alongside the metrics from the public test split, since
  visual review of failure cases matters as much as aggregate scores for judging
  detection and localisation quality before deployment
- Judge the limits of the approach: it is strong for screening and localising
  unusual regions but weak on defect taxonomy, root-cause attribution, and
  ERP-aligned defect codes, so plan threshold calibration, deployment export, or
  a supervised second-stage classifier as follow-up steps
- Organise scaling-up experiments on a GPU cluster by running one SLURM job per
  experiment and using job arrays to sweep categories, resolutions, and
  preprocessing choices

## Who is this for?

- Engineers and practitioners working on visual inspection in manufacturing and
  industrial settings
- Data scientists and ML practitioners looking for a practical anomaly detection
  workflow with public data

## Prerequisites

- Basic Python programming skills
- Familiarity with PyTorch fundamentals
- GPU access recommended for training
