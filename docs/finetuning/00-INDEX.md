# Fine-tuning Guide for La Biblioteca Eterna

This guide provides a comprehensive overview of fine-tuning Large Language Models (LLMs), specifically tailored for the "La Biblioteca Eterna" project. It covers the theoretical underpinnings, practical techniques, and project-specific considerations for fine-tuning the various LLMs used in the game.

## Table of Contents

1.  [Introduction to Fine-tuning](01-introduction.md)
    *   What is Fine-tuning?
    *   Why Fine-tune?
    *   Fine-tuning vs. Pre-training
    *   Fine-tuning vs. Prompt Engineering
    *   When to Fine-tune (and When Not To)

2.  [Fine-tuning Techniques](02-techniques.md)
    *   Full Fine-tuning
    *   Parameter-Efficient Fine-tuning (PEFT)
        *   LoRA (Low-Rank Adaptation)
        *   QLoRA (Quantized LoRA)
        *   Adapters
        *   Prefix Tuning
    *   Knowledge Distillation
        *   Teacher-Student Models
        *   Distillation Objectives
        *   Data Considerations

3.  [Data Preparation](03-data-preparation.md)
    *   Dataset Formats
        *   Instruction-Response Pairs
        *   Conversational Data
        *   Text Corpora
    *   Data Cleaning and Preprocessing
        *   Tokenization
        *   Handling Special Characters
        *   Length Considerations
    *   Data Augmentation
        *   Back Translation
        *   Synonym Replacement
        *   Random Insertion/Deletion
    *   Dataset Splitting (Train/Validation/Test)
    *   Data Quality and Bias Considerations

4.  [Training Process](04-training-process.md)
    *   Setting up the Environment (PyTorch, Transformers)
    *   Loading Pre-trained Models
    *   Configuring the Trainer
        *   Optimizers (AdamW, etc.)
        *   Learning Rate Schedulers
        *   Batch Size
        *   Gradient Accumulation
        *   Mixed Precision Training (FP16/BF16)
    *   Monitoring Training (TensorBoard, MLflow)
    *   Evaluation Metrics
        *   Perplexity
        *   BLEU Score
        *   ROUGE Score
        *   Custom Metrics (for La Biblioteca Eterna)
    *   Checkpointing and Saving Models

5.  [Fine-tuning for La Biblioteca Eterna](05-project-specific.md)
    *   Director LLM Fine-tuning
        *   Dataset Requirements
        *   Training Objectives
        *   Evaluation Strategies
    *   NPC Agent Fine-tuning
        *   Dataset Requirements
        *   Training Objectives
        *   Evaluation Strategies
    *   Book LLM Fine-tuning
        *   Dataset Requirements
        *   Training Objectives
        *   Evaluation Strategies
    *   Multi-Agent Considerations
    *   Iterative Fine-tuning and Refinement

6.  [Advanced Topics](06-advanced-topics.md)
    *   Catastrophic Forgetting
    *   Overfitting and Regularization
    *   Hyperparameter Optimization
    *   Distributed Training
    *   Continual Learning

7.  [Tools and Resources](07-tools-and-resources.md)
    *  Hugging Face Transformers
    *  PyTorch Lightning
    *  MLflow
    *  RunPod
    *  Relevant Research Papers 