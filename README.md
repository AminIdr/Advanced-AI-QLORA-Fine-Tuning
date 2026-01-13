# QLoRA Fine-Tuning of LLaMA Models: A Performance Analysis

**Authors:** Amine IDRISSI & Zakaria CHOUKRI

## Project Overview
This project presents a comprehensive comparative analysis between **Standard Full Fine-Tuning** and **Quantized Low-Rank Adaptation (QLoRA)** applied to Large Language Models (LLMs). 

Using **TinyLlama-1.1B** and the **WikiText-2** dataset, we evaluate the trade-offs between memory efficiency, computational speed, and model quality to determine the viability of training LLMs on consumer-grade hardware.

## Key Results Summary

Our experiments demonstrate that QLoRA achieves a **3.82x memory compression ratio** compared to standard fine-tuning.

| Metric | Standard Fine-Tuning | QLoRA | Improvement/Impact |
| :--- | :--- | :--- | :--- |
| **Model Size** | 2,098 MB | **548 MB** | 🟢 **-73.9% (Memory)** |
| **Trainable Params** | 1.1 Billion (100%) | **12.6 Million (1.15%)** | 🟢 **-98.85% (Params)** |
| **Inference Speed** | 33.12 tokens/sec | 10.62 tokens/sec | 🔴 **3.1x Slower** |
| **Perplexity (Quality)**| 18.42 | 21.87 | 🔴 **+18.73% (Degradation)** |

## Experimental Setup

*   **Model:** TinyLlama-1.1B-Chat-v1.0
*   **Dataset:** WikiText-2
*   **QLoRA Configuration:**
    *   Quantization: 4-bit NormalFloat (NF4) + Double Quantization
    *   LoRA Rank ($r$): 16
    *   LoRA Alpha ($\alpha$): 32
    *   Target Modules: All attention & feed-forward layers

## Key Observations

1.  **Memory Efficiency:** QLoRA makes it possible to fine-tune billion-parameter models on GPUs with limited VRAM (e.g., RTX 3090/4090) by freezing the base model and quantizing it to 4-bit.
2.  **Inference Latency:** There is a significant speed penalty (3x slower) during inference due to the on-the-fly dequantization overhead.
3.  **Compute Profile:** QLoRA is memory-bandwidth bound, resulting in lower Mean FLOPS Utilization (MFU) compared to full fine-tuning.

## Conclusion
QLoRA is an excellent solution for **research, prototyping, and memory-constrained environments**, democratizing access to LLM training. However, for production deployments requiring real-time low latency or maximum fidelity, standard fine-tuning or post-training quantization is preferred.
