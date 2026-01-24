---
title: "Carbon-Aware LLM Research"
permalink: /research/
author_profile: true
---
<br>

# Overview

Large Language Models (LLMs) are transforming AI, but their **energy use and carbon emissions** are substantial and growing. My research in this area develops **accurate carbon measurement, prediction, and optimization tools** that span model training, inference, and deployment — from cloud GPUs to edge processors. Rather than relying on coarse estimates, these works provide **system-aware, phase-aware, and hardware-calibrated frameworks** that enable practitioners and researchers to understand and reduce the environmental footprint of LLMs.

Key contributions include:
- End-to-end carbon modeling that integrates hardware utilization and embodied carbon.  
- Learned predictors that estimate inference carbon with high fidelity across configurations.  
- Estimators for edge LLM deployments that account for peripherals and embodied costs.

---

## LLMCarbon (ICLR 2024) — End-to-end carbon modeling

**Goal:** Provide an accurate, reusable framework to estimate **total carbon emissions** of LLMs before training begins.

**Approach:**  
- Parametric models linking LLM design (model size, architecture, MoE vs dense), execution (batch size, GPU utilization), and embodied hardware cost.  
- Combines operational energy measurements with amortized manufacturing carbon.

**Impact:**  
- Predicts pre-training carbon with improved accuracy compared to prior tools.  
- Helps designers explore **carbon–performance tradeoffs** early in model development.

**Artifact:**  
Code and datasets available at the **LLMCarbon** GitHub repository.

---

## LLMCO₂ (2024–2025) — Learned inference carbon prediction

**Goal:** Predict the **carbon cost of LLM inference** across diverse hardware and request patterns.

**Approach:**  
- Train a machine learning model (graph-based) to capture interactions between request characteristics (prompt length, batch size), model features (quantization, sparsity), and hardware performance patterns.  
- Evaluate on measured inference traces spanning multiple GPU types and workloads.

**Impact:**  
- Surpasses traditional formula-based estimators in prediction accuracy.  
- Enables **carbon-aware scheduling** for cloud and service deployments.

**Artifact:**  
Published as a dataset and predictor model in support of inference carbon estimation.

---

## CO2-Meter (AAAI 2026) — Carbon estimation for edge LLMs

**Goal:** Extend carbon estimation to **edge LLM inference**, where peripherals and embodied costs are significant.

**Approach:**  
- Modular estimator separating SoC operational energy, peripherals, and embodied amortization.  
- Models distinct execution phases (prefill, decode) and platform-specific overheads (NPU, GPU, quantized CPU).  
- Validated on a curated dataset of edge inference traces.

**Impact:**  
- Demonstrates that **peripherals and embodied costs** materially influence carbon rankings.  
- Provides actionable estimates for edge deployment decisions (e.g., local quantized model vs cloud offload).

**Artifact:**  
Public implementation and data preprocessing scripts released with the paper.

---

## Common Methods Across Works

- **Hardware-aware calibration:** Model carbon cost using real utilization and trace data from GPUs and edge SoCs.  
- **Phase awareness:** Separate modeling for training, inference prefill, and decode phases to capture utilization dynamics.  
- **End-to-end accounting:** Combine operational and embodied carbon to support realistic lifecycle comparisons.  
- **Reproducibility:** Publicly available code and datasets for estimation and evaluation.

---

## Practical Insights

- **Inference matters:** In many deployment scenarios, inference carbon rivals or exceeds training emissions.  
- **Phase and hardware context are critical:** Simple FLOPS-based formulas are insufficient for consistent prediction across configurations.  
- **Embodied carbon influences decisions:** Particularly on edge devices and in long-running deployments, amortized manufacturing impact changes optimal choices.

---

## Links & Artifacts

- **LLMCarbon (ICLR 2024):** Model repository and documentation.  
- **LLMCO₂:** Predictor models and dataset for inference carbon.  
- **CO2-Meter (AAAI 2026):** Edge estimator code and dataset.