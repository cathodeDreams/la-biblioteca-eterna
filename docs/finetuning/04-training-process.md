# 4. Training Process

This section outlines the practical steps involved in fine-tuning an LLM.

## Setting up the Environment (PyTorch, Transformers)

*   **Install PyTorch:** Follow the instructions on the official PyTorch website ([https://pytorch.org/](https://pytorch.org/)) to install the appropriate version for your system (with CUDA support if you have an NVIDIA GPU).
*   **Install Hugging Face Transformers:** `pip install transformers`
*   **Install other libraries:** `pip install datasets accelerate tensorboard mlflow` (datasets for loading datasets, accelerate for distributed training, tensorboard for monitoring, mlflow for experiment tracking)

## Loading Pre-trained Models

```python
from transformers import AutoModelForCausalLM, AutoTokenizer

model_name = "mistralai/Mistral-7B-v0.1"  # Example: Replace with your desired model

model = AutoModelForCausalLM.from_pretrained(model_name)
tokenizer = AutoTokenizer.from_pretrained(model_name)

# If using LoRA, apply LoRA configuration here
from peft import LoraConfig, get_peft_model

config = LoraConfig(
    r=8, # Rank
    lora_alpha=32, # Scaling factor
    target_modules=["q_proj", "v_proj"], # Example: Target attention layers
    lora_dropout=0.1,
    bias="none",
    task_type="CAUSAL_LM"
)

model = get_peft_model(model, config)
```

## Configuring the Trainer

The Hugging Face `Trainer` class simplifies the training process.

```python
from transformers import TrainingArguments, Trainer

training_args = TrainingArguments(
    output_dir="./results",          # Where to save checkpoints
    num_train_epochs=3,              # Number of training epochs
    per_device_train_batch_size=4,   # Batch size per GPU
    per_device_eval_batch_size=8,    # Batch size for evaluation
    gradient_accumulation_steps=2,  # Accumulate gradients over multiple steps
    evaluation_strategy="steps",     # Evaluate every `eval_steps`
    eval_steps=500,                 # Evaluation frequency
    save_steps=1000,                # Save checkpoint frequency
    learning_rate=2e-5,             # Learning rate
    weight_decay=0.01,              # Weight decay (regularization)
    warmup_steps=500,               # Warmup steps for learning rate scheduler
    logging_dir="./logs",           # Directory for logs
    logging_steps=10,               # Log every 10 steps
    fp16=True,                     # Use mixed precision training (if supported)
    # bf16=True,                   # Use bfloat16 (if supported - Ampere+ GPUs)
    report_to="tensorboard",        # Report to TensorBoard
)

trainer = Trainer(
    model=model,
    args=training_args,
    train_dataset=train_dataset,  # Your training dataset
    eval_dataset=eval_dataset,    # Your evaluation dataset
    tokenizer=tokenizer,
)

trainer.train()
```

### Optimizers (AdamW, etc.)

*   **AdamW:** A commonly used optimizer that often performs well for fine-tuning LLMs.
*   **Learning Rate:** A crucial hyperparameter that controls the step size during optimization.  Start with a small learning rate (e.g., 2e-5) and experiment.

### Learning Rate Schedulers

*   **Warmup:** Gradually increase the learning rate at the beginning of training to avoid instability.
*   **Linear Decay:** Gradually decrease the learning rate over time.
*   **Cosine Annealing:**  A more sophisticated scheduler that can improve performance.

### Batch Size

*   The number of samples processed in each iteration.  Larger batch sizes can speed up training but require more memory.

### Gradient Accumulation

*   Allows you to effectively increase the batch size even if your GPU memory is limited.  Gradients are accumulated over multiple steps before updating the model weights.

### Mixed Precision Training (FP16/BF16)

*   Uses lower-precision floating-point numbers (FP16 or BF16) to reduce memory usage and speed up training.  Requires compatible hardware (recent NVIDIA GPUs).

## Monitoring Training (TensorBoard, MLflow)

*   **TensorBoard:**  A visualization toolkit for monitoring training progress (loss curves, learning rate, etc.).  Launch with `tensorboard --logdir=./logs`.
*   **MLflow:**  A platform for managing the machine learning lifecycle, including experiment tracking, model versioning, and deployment.

## Evaluation Metrics

### Perplexity

*   A measure of how well the model predicts the next token in a sequence.  Lower perplexity is better.

### BLEU Score

*   A metric for evaluating machine translation quality.  Measures the overlap between the model's output and a reference translation.

### ROUGE Score

*   Another metric for evaluating text summarization and machine translation.  Measures the overlap of n-grams between the model's output and a reference.

### Custom Metrics (for La Biblioteca Eterna)

*   **Relevancy:**  How relevant is the generated text to the current context (e.g., the current book, conversation, or location in the library)?
*   **Coherence:**  How coherent and logical is the generated text?
*   **Style Consistency:**  Does the generated text match the expected style (e.g., the style of a particular book or NPC)?
*   **Insightfulness:**  Does the generated text contribute to the player's understanding and *revelaciones*? (This is a more subjective metric that might require human evaluation.)

## Checkpointing and Saving Models

*   The `Trainer` automatically saves checkpoints at regular intervals (specified by `save_steps`).
*   You can also manually save the model and tokenizer:

```python
model.save_pretrained("./my_fine_tuned_model")
tokenizer.save_pretrained("./my_fine_tuned_model")
``` 