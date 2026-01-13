# QLoRA vs Standard Fine-Tuning Comparison

A comprehensive Jupyter notebook comparing **QLoRA** (Quantized Low-Rank Adaptation) with standard full fine-tuning on LLaMA models.

## Overview

This project demonstrates how QLoRA achieves significant memory efficiency gains while maintaining model quality through:
- **4-bit quantization** (NF4 format)
- **Low-rank adapters** (LoRA)
- Efficient parameter training

## Key Metrics

| Metric | Standard FT | QLoRA | Improvement |
|--------|-------------|-------|-------------|
| **Trainable Parameters** | 1.1B | ~12.6M | 99.9% fewer |
| **Model Size** | 2.1 GB | ~0.6 GB | 3.5x smaller |
| **Training Speed** | Baseline | Variable | Up to 50% faster |
| **Inference Speed** | Baseline | Similar | Comparable |
| **Memory Savings** | - | - | ~71% reduction |

## Dataset & Model

- **Model**: TinyLlama-1.1B-Chat-v1.0
- **Dataset**: WikiText-2-raw-v1 (36,718 training samples)
- **Task**: Autoregressive language modeling
- **Training Steps**: 500

## Features

✓ Side-by-side performance benchmarking  
✓ FLOPS and MFU (Mean FLOPS Utilization) analysis  
✓ Perplexity and inference time measurements  
✓ Comprehensive visualization (6-panel comparison + radar chart)  
✓ Memory compression analysis  

## Use Cases

- Fine-tune large models on **consumer GPUs**
- Reduce **cloud compute costs**
- Faster **experimentation cycles**
- Enable **edge deployment**

## Files

- `llama_qlora_finetuning.ipynb` - Main notebook (12 sections, 38 cells)
- `qlora_comparison.png` - 6-panel comparison charts
- `qlora_radar.png` - Normalized performance radar chart
- `qlora_metrics_comparison.csv` - Detailed metrics export

## Requirements
