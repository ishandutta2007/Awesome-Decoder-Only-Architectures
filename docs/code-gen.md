# Code Generation Models

Code generation models specialize in understanding and synthesizing programming languages. While they are built on the same decoder-only foundation as LLMs, they often employ specific techniques to handle the structured nature of code.

## Core Mechanism: Fill-in-the-Middle (FIM)

Standard causal models can only predict what comes *after* a given prefix. However, developers often need to insert code in the middle of an existing file. **FIM** rearranges the training data so the model learns to bridge the gap between a prefix and a suffix.

### Diagram: FIM Logic
<p align="center">
<svg width="500" height="200" xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="#e9ecef"/>
  
  <!-- Boxes -->
  <rect x="20" y="50" width="100" height="40" rx="5" fill="#51cf66" stroke="#2b8a3e"/>
  <text x="40" y="75" fill="white" font-family="Arial" font-weight="bold">Prefix</text>
  
  <rect x="140" y="50" width="100" height="40" rx="5" fill="#ff922b" stroke="#d9480f"/>
  <text x="160" y="75" fill="white" font-family="Arial" font-weight="bold">Middle</text>
  
  <rect x="260" y="50" width="100" height="40" rx="5" fill="#339af0" stroke="#1971c2"/>
  <text x="280" y="75" fill="white" font-family="Arial" font-weight="bold">Suffix</text>
  
  <text x="370" y="75" font-family="Arial" font-size="20">➔</text>
  
  <!-- Rearranged -->
  <rect x="20" y="130" width="400" height="50" rx="5" fill="white" stroke="#333"/>
  <text x="30" y="160" font-family="Courier" font-size="12">[PRE] Prefix [SUF] Suffix [MID] Middle</text>
  
  <text x="20" y="30" font-family="Arial" font-size="14" font-weight="bold">Original Code</text>
  <text x="20" y="115" font-family="Arial" font-size="14" font-weight="bold">Training Sequence (FIM)</text>
</svg>
</p>

## Key Characteristics
- **Long Context Windows:** Essential for understanding large codebases.
- **Structured Awareness:** Better handling of indentation and syntax.
- **Repository-Level Reasoning:** Using RAG or fine-tuning to understand project-specific patterns.

## Historical Context
The **StarCoder** and **CodeLlama** papers (2022-2023) popularized the FIM objective, making it the industry standard for code completion models.

[Back to README](../README.md)
