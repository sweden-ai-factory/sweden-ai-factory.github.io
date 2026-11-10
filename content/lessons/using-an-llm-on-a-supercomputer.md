+++
title = "Using an LLM on a supercomputer"
description = "Short tutorial on compiling and serving llama.cpp on the LUMI supercomputer, from building the backend for AMD GPUs to reaching the model from your own laptop over an SSH tunnel."

[taxonomies]
skill = ["hpc", "ai", "gen_ai"]
difficulty = ["intermediate"]
maturity = ["stable"]

[extra]
tags = ["short-tutorial", "llama.cpp", "llm", "slurm", "amd", "gpu", "rocm", "huggingface"]
external_url = "https://swedenaifactory.se/short-tutorials/2026/03/using-an-llm-on-a-supercomputer/"
+++

## Overview

This short tutorial walks through hosting an LLM on a supercomputer using `llama.cpp`, covering the full pipeline from compiling the backend for AMD GPUs (ROCm/HIP) to serving the model and connecting to it from your local machine. While it targets the LUMI supercomputer, the approach generalises to other Slurm-based HPC systems, and it uses the Hugging Face Hub to fetch quantized GGUF models.

## Key takeaways

- How to compile `llama.cpp` with Ninja for AMD GPUs (gfx90a / MI250X) and adapt the build for NVIDIA GPUs or Vulkan
- How to request compute resources with `salloc`/`sbatch` and structure a Slurm job script for a model server
- How to obtain and quantize models via `huggingface-hub` (GGUF format) and serve them with `llama-server`
- How to open an SSH tunnel so a remote supercomputer model is reachable from `localhost`, like any local endpoint

## Who is this for?

- Researchers and engineers who want to run LLM inference on HPC systems
- Users of Slurm-based clusters (LUMI, Leonardo, Meluxina) with basic Linux shell familiarity

## Prerequisites

- Access to an HPC system (e.g. LUMI) with a Slurm account and project allocation
- Basic Linux/shell competence and comfort editing the supplied job scripts
- Optional: familiarity with Git and Python virtual environments for model downloads
