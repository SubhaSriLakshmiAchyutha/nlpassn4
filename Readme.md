## Q1 – Character-Level RNN Language Model 

In this question, I implemented a character-level RNN that predicts the next character in a sequence. I first prepared a small toy dataset using short words such as “hello” and “help”, and later added a larger text file to expose the model to more patterns. All characters were mapped to integer IDs to form a vocabulary.

I constructed training sequences where the input is a series of characters and the target is the same sequence shifted by one step, enabling the model to learn next-character prediction. The model architecture consisted of:

Embedding layer – converts character IDs into dense vector representations
RNN/GRU/LSTM layer – models temporal dependencies in the character sequence
Linear layer – outputs logits over all possible characters

The model was trained with teacher forcing, using cross-entropy loss to compare predictions with the true next characters. After training, I implemented a sampling function that generates text given a starting character. I experimented with different temperature values, where low temperature produced more deterministic outputs and high temperature introduced more randomness.

## Q2 – Toy Self-Attention

In this question, I implemented a small demonstration of self-attention. I created several short sentences, tokenized them by splitting on spaces, and built a word-level vocabulary. Because the sentences had different lengths, I padded them to create a uniform batch.

Each token was passed through an embedding layer, and I manually computed the Query (Q), Key (K), and Value (V) vectors required for attention. Using these, I applied the scaled dot-product attention formula to determine how strongly each word attends to the others in the same sentence.

To visualize the results, I selected one sentence and one attention head, extracted its attention matrix, and plotted it as a heatmap. The heatmap illustrates the attention distribution: brighter cells indicate higher attention weights, while darker cells represent lower weights. This visualization helps interpret which words influence each other during processing.

## Q3 – Scaled Dot-Product Attention

For this question, I implemented scaled dot-product attention from first principles. I created random matrices for Q (queries), K (keys), and V (values) and then applied the standard attention procedure:

Compute raw attention scores and Scale the scores by to prevent large values from making the softmax unstable.

Apply softmax to convert the scores into normalized attention weights.

Multiply the attention weights by 𝑉 - V to obtain the final output vectors.

To illustrate the effect of each step, I printed the raw scores before scaling, the scaled scores, the attention weights after softmax, and the final outputs. This made it clear how scaling helps stabilize the distribution and leads to smoother, more meaningful attention weights.