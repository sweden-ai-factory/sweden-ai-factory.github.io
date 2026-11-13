+++
title = "Using an LLM on a supercomputer"
description = "Short tutorial on compiling llama.cpp for AMD GPUs and serving an LLM on the LUMI supercomputer, then accessing it from your laptop over an SSH tunnel."

[taxonomies]
skill = ["hpc", "ai", "gen_ai"]
difficulty = ["intermediate"]
maturity = ["stable"]

[extra]
tags = ["short-tutorial", "llama.cpp", "llm", "slurm", "amd", "gpu", "rocm", "huggingface"]
external_url = "https://swedenaifactory.se/short-tutorials/2026/03/using-an-llm-on-a-supercomputer/"
+++

## Overview

This short tutorial walks through hosting an LLM on a supercomputer using
`llama.cpp`, covering the full pipeline from compiling the backend for AMD GPUs
(ROCm/HIP) to serving the model and connecting to it from your local machine.
While it targets the LUMI supercomputer, the approach is roughly the same on
other Slurm-based systems such as Leonardo and Meluxina, with minor changes
(e.g. loading different modules), and it uses the Hugging Face Hub to fetch
quantized GGUF models.

## Key takeaways

- Build `llama.cpp` with Ninja for AMD GPUs (ROCm/HIP, gfx90a / MI250X) and see
  how the build differs for NVIDIA GPUs (`-DGGML_CUDA=ON`) or a cross-platform
  Vulkan target
- Request an interactive GPU session with `salloc` to compile, then structure a
  Slurm batch script (`sbatch`) that launches `llama-server` on a compute node
- Obtain pre-quantized GGUF models from the Hugging Face Hub via
  `huggingface-hub` and serve them with `llama-server`
- Reach the served model from your local machine over an SSH tunnel, so a
  supercomputer-hosted endpoint behaves like any local server

## Who is this for?

- Researchers and engineers who want to run LLM inference on HPC systems
- Users of Slurm-based clusters (LUMI, Leonardo, Meluxina) with basic Linux
  shell familiarity

## Prerequisites

- Access to an HPC system (e.g. LUMI) with a Slurm account and project
  allocation
- A project or scratch directory on the HPC system for compiling and storing
  models (home directories have strict quotas)
- Basic Linux/shell competence and comfort editing the supplied job scripts
- Optional: familiarity with Git and Python virtual environments for model
  downloads
