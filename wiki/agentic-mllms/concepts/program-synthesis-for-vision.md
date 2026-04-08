---
topic: agentic-mllms
tags: [concept, method]
---

## Definition

Program synthesis for vision is the automatic generation of executable programs (typically Python code) that solve visual reasoning tasks by composing sequences of vision and language operations. The generated program directly executes on visual inputs to produce structured results, making each step interpretable and debuggable.

## Origins

Rooted in neural module networks and neuro-symbolic reasoning, but modernized by leveraging code-capable LLMs (GPT-3 Codex). ViperGPT demonstrates that LLMs trained on code can effectively synthesize visual programs without explicit supervision, by providing them with an API specification and a natural language query.

## Key variants / extensions

- **Unrestricted Python code**: ViperGPT generates full Python with control flow, loops, and mathematical operations, allowing arbitrary composition
- **Pseudocode / symbolic instructions**: Concurrent approaches generate higher-level pseudocode or structured lists of instructions rather than executable code
- **In-context learning**: Some systems demonstrate program synthesis through examples rather than API specifications
- **Constrained synthesis**: Techniques that restrict the program space to improve reliability or enforce certain properties

## Papers using this concept

- [[../papers/2023-viper-gpt|ViperGPT]] — demonstrates code generation as a flexible interface for composing vision modules; zero-shot reasoning via Python execution
