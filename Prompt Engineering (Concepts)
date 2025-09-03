1. Role Assignment (Persona Prompts)  

  Assigning the model a role (“You are a senior software engineer reviewing code”) dramatically shapes tone, depth, and accuracy.
  Works because LLMs adjust responses based on implied identity, aligning with training distributions.

2. Instruction Hierarchies (System → Context → User)

  Use layered instructions: system-level framing → context/background → precise user query.
  Ensures models prioritize high-level goals while respecting task details.

3. Few-Shot Prompting (Exemplar Priming)

  Show the model a few high-quality input/output examples.
  Builds an implicit program inside the LLM’s context window, strongly influencing style, format, and logic.

4. Chain of Thought (CoT) & Step Decomposition

  Asking the model to reason step by step before answering improves accuracy on math, logic, and planning tasks.
  Advanced form: Tree of Thought or Graph of Thought (branching reasoning).

5. Self-Consistency & Multiple Generations

  Instead of one answer, sample multiple responses with randomness, then aggregate (e.g., majority vote).
  Proven in research (Wang et al., 2022) to boost accuracy in reasoning-heavy tasks.

6. Instructional Scaffolding (Meta-Prompting)

  Break complex tasks into sub-prompts (e.g., summarize → critique → refine).
  Mirrors human curriculum learning and helps avoid error propagation.

7. Context Window Optimization

  Order matters: put the most important instructions/examples at the end (recency bias).
  Use compression (summaries, embeddings) to fit longer contexts.

8. Formatting Bias (Structured Outputs)

  Ask for structured formats (Markdown, JSON, tables).
  Leverages the model’s learned bias toward patterns and reduces hallucinations.
