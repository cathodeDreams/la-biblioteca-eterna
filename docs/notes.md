# Notes

## Links

### libtcod

https://libtcod.readthedocs.io/en/latest/

https://libtcod.github.io/docs/

### llama-cpp-python

https://github.com/abetlen/llama-cpp-python

https://github.com/abetlen/llama-cpp-python/tree/main/examples

## Papers

### 1. Model Distillation and Compression

- [**Distilling the Knowledge in a Neural Network (Hinton et al., 2015)**](https://arxiv.org/pdf/1503.02531.pdf)
- [**FitNets: Hints for Thin Deep Nets (Romero et al., 2014)**](https://arxiv.org/pdf/1412.6550.pdf)
- [**Born-Again Neural Networks (Furlanello et al., 2018)**](https://arxiv.org/pdf/1805.04770.pdf)
- [**A Survey on Model Compression for Large Language Models**](https://direct.mit.edu/tacl/article-pdf/125482/A-Survey-on-Model-Compression-for-Large-Language.pdf)
- [**Techniques to Make Large Language Models Smaller: An Explainer**](https://cset.georgetown.edu/wp-content/uploads/CSET-Techniques-to-Make-Large-Language-Models-Smaller-An-Explainer.pdf)

---

### 2. Knowledge Distillation for Compressing Large Models

- [**KD-LoRA: A Hybrid Approach to Efficient Fine-Tuning with LoRA and Knowledge Distillation**](https://arxiv.org/pdf/2410.20777.pdf)

---

### 3. LoRA and Related Techniques

- [**LoRA: Low-Rank Adaptation of Large Language Models (Hu et al., 2021)**](https://arxiv.org/pdf/2106.09685.pdf)
- [**PC-LoRA: Low-Rank Adaptation for Progressive Model Compression with Knowledge Distillation**](https://arxiv.org/pdf/2406.09117.pdf)

---

### 4. QLoRA and Parameter-Efficient Fine-Tuning (PEFT)

- [**QLoRA: Efficient Finetuning of Quantized LLMs**](https://arxiv.org/pdf/2305.14314.pdf)
- [**Parameter-Efficient Transfer Learning for NLP (Houlsby et al., 2019)**](https://arxiv.org/pdf/1902.00751.pdf)

---

### 5. Domain-Specific Training and Domain Adaptation

- [**Don't Stop Pretraining: Adapt Language Models to Domains and Tasks (Gururangan et al., 2020)**](https://arxiv.org/pdf/2004.07690.pdf)
- [**Efficient Continual Pre-training for Building Domain Specific Large Language Models**](https://arxiv.org/pdf/2311.08545.pdf)

---

For efficient training infrastructure, please refer to the online documentation for:
- [Lightning AI – Training Models with Billions of Parameters](https://lightning.ai/docs/pytorch/stable/advanced/model_parallel/index.html)
- [PyTorch Lightning Documentation](https://pytorch-lightning.readthedocs.io/)
- [MLflow](https://mlflow.org/)
- [DVC](https://dvc.org/)

## Iterative prompt instructions

### 1. Read the last conversation and append to context documentation

```
Carefully read the provided context. 

Update technical_report.md and README.md to account for the project's current status.
```

### 2. Read the context documentation and choose the next step.

```
Carefully read the provided context.

Choose what to work on from the Next Steps section of the technical report and implement with tests.
```

### 3. Read the test results and systematically fix.
    
```
Carefully read the test results.

Systematically fix the issues.
```