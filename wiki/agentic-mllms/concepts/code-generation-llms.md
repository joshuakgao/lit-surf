---
topic: agentic-mllms
tags: [concept, architecture]
---

## Definition

Code-generation LLMs are large language models trained on vast repositories of source code from the internet, enabling them to generate syntactically and semantically correct executable programs. Examples include GPT-3 Codex, Codex, PaLM-Coder. These models learn strong priors about logical composition, control flow, API usage, and mathematical reasoning through exposure to millions of code examples.

## Origins

Emerged from scaling trends in language modeling; Codex (Chen et al., 2021) demonstrated that a GPT-3 variant trained on code could solve programming problems in natural language. Building on this, researchers began applying code-generation LLMs to non-traditional programming tasks, including visual reasoning.

## Key capabilities

- **API usage**: Learns patterns for calling functions with appropriate arguments
- **Control flow**: Understands loops, conditionals, and nested logic
- **Composition**: Synthesizes sequences of function calls in sensible order
- **Mathematical reasoning**: Integrates symbolic operators (arithmetic, comparisons) with learned concepts
- **Debugging awareness**: Can self-correct simple errors or generate error-handling code

## Papers using this concept

- [[../papers/2023-viper-gpt|ViperGPT]] — leverages GPT-3 Codex to generate Python programs that compose vision modules; demonstrates that code generation is a flexible interface for program synthesis
