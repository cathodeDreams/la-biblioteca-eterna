# 5. Fine-tuning for La Biblioteca Eterna

This section details the specific fine-tuning strategies for each type of LLM in La Biblioteca Eterna.

## Director LLM Fine-tuning

### Dataset Requirements

*   **Narrative Examples:**  Examples of desired narrative structures, including descriptions of library sections, events, and NPC interactions.  These should be written in the style and tone of the game.
*   **Game Master Guides:**  Adaptations of tabletop RPG game master guides, focusing on creating a sense of mystery, exploration, and intellectual discovery.
*   **Interactive Fiction:**  Examples of interactive fiction (text adventures) that demonstrate how to handle player choices and generate dynamic responses.
*   **Instruction-Response Pairs:**  Specific instructions for the Director LLM, such as "Generate a description of a hidden chamber containing a rare book" or "Introduce a new NPC who is a scholar of ancient languages."
*   **Dialogue Examples:** Examples of conversations between the player and NPCs, demonstrating how the Director LLM should guide the dialogue.

### Training Objectives

*   **Narrative Coherence:**  The Director LLM should generate text that is consistent with the overall narrative and game state.
*   **Player Agency:**  The Director LLM should respond appropriately to player choices and actions.
*   **Atmosphere and Tone:**  The generated text should maintain the game's atmosphere of mystery, contemplation, and intellectual discovery.
*   **Knowledge Integration:**  The Director LLM should seamlessly integrate information from the knowledge base into the narrative.

### Evaluation Strategies

*   **Perplexity:**  Measure the model's ability to predict the next token in narrative sequences.
*   **Human Evaluation:**  Crucial for assessing the quality of the narrative, the responsiveness to player actions, and the overall atmosphere.
*   **Custom Metrics:**
    *   **Relevancy:**  How well does the generated text relate to the current game state and player actions?
    *   **Coherence:**  Is the narrative logical and consistent?
    *   **Engagement:**  Does the narrative keep the player engaged and motivated to explore?
    *   **Insightfulness:**  Does the narrative contribute to the player's understanding and *revelaciones*?

## NPC Agent Fine-tuning

### Dataset Requirements

*   **Character Profiles:**  Detailed descriptions of each NPC, including their personality, background, knowledge, and motivations.
*   **Dialogue Examples:**  Conversations between the NPC and the player, demonstrating the NPC's personality and conversational style.  These should be tailored to the NPC's role and knowledge.
*   **Role-Specific Interactions:**  Examples of how the NPC interacts with the environment and other NPCs.
*   **Instruction-Response Pairs:** Specific instructions for the NPC, such as "Answer a question about the history of this library section" or "Offer the player a cryptic clue."

### Training Objectives

*   **Personality Consistency:**  The NPC should maintain a consistent personality and conversational style.
*   **Knowledge Accuracy:**  The NPC should provide accurate information based on their knowledge domain.
*   **Engaging Dialogue:**  The NPC should engage in meaningful and interesting conversations with the player.
*   **Responsiveness:** The NPC should respond appropriately to player questions and actions.

### Evaluation Strategies

*   **Perplexity:** Measure the model's ability to predict the next token in dialogue sequences.
*   **Human Evaluation:**  Essential for assessing the believability of the NPC, the quality of the dialogue, and the overall interaction.
*   **Custom Metrics:**
    *   **Personality Adherence:**  Does the NPC's dialogue match their defined personality?
    *   **Knowledge Accuracy:**  Is the information provided by the NPC correct?
    *   **Engagement:**  Does the conversation keep the player engaged?
    *   **Helpfulness:**  Does the NPC provide useful information or guidance to the player?

## Book LLM Fine-tuning

### Dataset Requirements

*   **Domain-Specific Texts:**  Excerpts from books, articles, and other texts related to the book's subject matter (e.g., philosophy, history, science, etc.).
*   **Summaries and Analyses:**  Summaries and analyses of the book's content, to help the LLM understand the key concepts.
*   **Instruction-Response Pairs:**  Specific instructions for the Book LLM, such as "Summarize the main argument of this chapter" or "Explain a specific concept from the book."
* **Stylistic Examples:** If a book has a particular writing style, provide examples to the model.

### Training Objectives

*   **Content Accuracy:**  The Book LLM should accurately represent the content of the book.
*   **Style Consistency:**  The generated text should match the style of the book (if applicable).
*   **Clarity and Conciseness:**  The Book LLM should provide clear and concise explanations of complex concepts.
*   **Knowledge Retrieval:** The model should be able to retrieve specific information from the book based on player queries.

### Evaluation Strategies

*   **Perplexity:** Measure the model's ability to predict the next token in text excerpts from the book.
*   **ROUGE/BLEU:**  Compare the model's summaries to human-written summaries.
*   **Human Evaluation:**  Assess the accuracy, clarity, and style of the generated text.
*   **Custom Metrics:**
    *   **Content Accuracy:**  Does the generated text accurately reflect the book's content?
    *   **Style Matching:**  Does the generated text match the book's style?
    *   **Clarity:**  Is the generated text easy to understand?
    *   **Completeness:** Does the model provide sufficient detail when answering questions?

## Multi-Agent Considerations

*   **Coordination:** The Director LLM needs to coordinate the actions and interactions of the NPC agents.
*   **Memory Management:**  The Director LLM needs to manage the memories of the NPC agents, ensuring consistency and preventing conflicts.
*   **Knowledge Sharing:**  The Director LLM needs to determine how knowledge is shared between the different agents.
*   **Iterative Fine-tuning:** Fine-tune the models iteratively, starting with individual models and then fine-tuning them together to improve their interactions.

## Iterative Fine-tuning and Refinement

*   **Start with individual fine-tuning:** Fine-tune each model (Director, NPCs, Books) separately.
*   **Then, fine-tune for interaction:**  Create scenarios where the models interact and fine-tune them based on the results.
*   **Continuously evaluate and refine:**  Use human evaluation and custom metrics to identify areas for improvement and iterate on the fine-tuning process.
*   **Use a Test-Driven Development (TDD) approach:** Create test cases to ensure that the models behave as expected and to prevent regressions.

This iterative approach is crucial for creating a cohesive and believable multi-agent system. 