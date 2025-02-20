# 3. Data Preparation

Data preparation is arguably the *most* critical aspect of fine-tuning. The quality, format, and relevance of your data will directly impact the performance of your fine-tuned models.

## Dataset Formats

The format of your data depends on the specific task you're fine-tuning for. Here are some common formats:

### Instruction-Response Pairs

This is a common format for fine-tuning models for specific tasks, like question answering or instruction following.

```json
[
    {
        "instruction": "Write a short poem about a lost soul in a library.",
        "response": "Through endless shelves, a spirit glides,\n..."
    },
    {
        "instruction": "Describe the architecture of a Spanish monastery library.",
        "response": "High vaulted ceilings, arches grand,\n..."
    }
]
```

### Conversational Data

This format is used for fine-tuning models for dialogue and conversation.

```json
[
    {
        "messages": [
            {"role": "user", "content": "Tell me about this library."},
            {"role": "assistant", "content": "This library is a repository of all knowledge..."},
            {"role": "user", "content": "Who else is here?"},
            {"role": "assistant", "content": "Many lost souls, seeking understanding..."}
        ]
    }
]
```

### Text Corpora

For fine-tuning on a specific style or domain, you can use a corpus of text.

```
This is a paragraph from a book about ancient philosophy.
This is another paragraph, discussing the nature of consciousness.
...
```

## Data Cleaning and Preprocessing

### Tokenization

*   **What it is:**  Converting text into numerical representations (tokens) that the LLM can understand.
*   **How it's done:**  Using a tokenizer specific to the pre-trained model you're using (e.g., the tokenizer from the Hugging Face Transformers library).
*   **Example:**  The sentence "The library is vast." might be tokenized into IDs like `[101, 1996, 3075, 2003, 6312, 1012]`.

### Handling Special Characters

*   **Problem:**  Special characters (e.g., unusual punctuation, non-ASCII characters) can cause issues if not handled correctly.
*   **Solution:**  Ensure your tokenizer is configured to handle these characters appropriately, or preprocess your data to replace or remove them.

### Length Considerations

*   **Problem:**  LLMs have a maximum input sequence length.  Longer sequences need to be truncated or handled specially.
*   **Solution:**  Truncate long sequences (losing information) or use techniques like sliding windows to process long texts in chunks.  For La Biblioteca Eterna, consider how to handle long book excerpts.

## Data Augmentation

Data augmentation techniques can help improve the robustness and generalization of your fine-tuned models, especially when you have limited data.

### Back Translation

*   **How it works:**  Translate your text into another language and then back to the original language. This can create variations in phrasing while preserving the meaning.
*   **Example:**  "The library is vast." -> (French) "La bibliothèque est vaste." -> (English) "The library is huge."

### Synonym Replacement

*   **How it works:**  Replace words with their synonyms.
*   **Example:**  "The ancient book was fascinating." -> "The old book was intriguing."

### Random Insertion/Deletion

*   **How it works:**  Randomly insert or delete words in the text.  Use this with caution, as it can easily introduce errors.

## Dataset Splitting (Train/Validation/Test)

*   **Training Set:**  The data used to train the model.
*   **Validation Set:**  Used to tune hyperparameters and monitor training progress.
*   **Test Set:**  Used to evaluate the final performance of the model.  *Never* use the test set during training or hyperparameter tuning.
*   **Typical Split:**  80/10/10 or 70/15/15.

## Data Quality and Bias Considerations

*   **Data Quality:**  Ensure your data is accurate, consistent, and free of errors.  Garbage in, garbage out!
*   **Bias:**  Be aware of potential biases in your data.  If your data reflects societal biases, your fine-tuned model will likely inherit those biases.  For La Biblioteca Eterna, consider potential biases in historical texts or philosophical viewpoints.

For La Biblioteca Eterna, data preparation will involve:

*   **Creating instruction-response pairs** for the Director LLM to guide the narrative.
*   **Collecting and formatting conversational data** for NPC interactions.
*   **Curating a corpus of text** from relevant domains (philosophy, history, literature) for the Book LLMs.
*   **Carefully cleaning and preprocessing** the data to ensure consistency and handle special characters.
*   **Using data augmentation** to expand the dataset and improve robustness.
*   **Addressing potential biases** in the source material. 