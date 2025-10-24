GPT : Generative Pretrained Transformer

# Generative:
   Creates new outputs (text, code, images) rather than just classifying.
   Example: writing a story, summarizing, generating code.

# Pre-Trained:
  Trained on massive datasets (web, books, code) to learn language patterns.
  Imagine building a universal brain that knows how to read, write, and talk about almost anything. This is done once, at great cost, by companies like OpenAI, Anthropic, or Meta.
  Unsupervised generative pretraining
  No human labels are provided — it just learns from raw text (unsupervised).
  Back Propagation (re-adjustment)
  Backpropagation is the engine under the hood that makes unsupervised learning possible. Every time GPT guesses the next word, backprop tweaks billions of parameters so the next guess is better.
  Reinforcement learning with human feedback (RLHF)
  After pre-training, the model is fine-tuned with human help.

# Transformer:
  It’s the neural network architecture that powers GPT.
  Transformers are built on a concept called self-attention, which lets the model decide:
  “While reading this sentence, which words should I pay the most attention to/matter most?”
  Key Parts of a Transformer (basic terms)
  Embedding Layer

Converts words → numbers (vectors).


Example: “dog” might become [0.13, 0.75, -0.44,…].
https://platform.openai.com/tokenizer 
It’s the entry point. GPT cannot work with raw words; it needs numbers that encode meaning and relationships.
Analogy:
Like translating words into coordinates on a map — “dog” and “puppy” will be near each other, “dog” and “car” farther apart.
 Positional Encoding → adds word order
 Self-Attention → links words by importance
 Feed-Forward Network → transforms meaning per token
 Residual Connections + Normalization → stable training
 Decoder Stacks (in GPT) → predicts next word step by step


# Models:
https://platform.openai.com/docs/models 

