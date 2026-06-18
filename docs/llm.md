# Large Language Models (LLMs)

Large Language Models are the most prominent application of decoder-only transformer architectures. They are trained to predict the next token in a sequence given all previous tokens.

## Core Mechanism: Causal Masking

The fundamental innovation in LLMs is the use of **Causal Masked Self-Attention**. In a standard transformer encoder, every token can attend to every other token. In a decoder-only LLM, a mask is applied to the attention matrix to ensure that token $i$ can only attend to tokens $j \le i$.

### Diagram: Masked Attention
<p align="center">
<svg width="400" height="200" xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="#f8f9fa"/>
  <!-- Matrix grid -->
  <rect x="50" y="50" width="100" height="100" fill="white" stroke="#333"/>
  <line x1="50" y1="100" x2="150" y2="100" stroke="#ccc"/>
  <line x1="100" y1="50" x2="100" y2="150" stroke="#ccc"/>
  
  <!-- Causal Mask -->
  <path d="M 100 50 L 150 50 L 150 100 Z" fill="#ff6b6b" opacity="0.5"/>
  <text x="160" y="80" font-family="Arial" font-size="12" fill="#ff6b6b">Masked (Future)</text>
  
  <!-- Tokens -->
  <text x="60" y="170" font-family="Arial" font-size="14">Token 1</text>
  <text x="110" y="170" font-family="Arial" font-size="14">Token 2</text>
  
  <text x="10" y="80" font-family="Arial" font-size="14" transform="rotate(-90 10,80)">Attention</text>
  
  <rect x="250" y="50" width="120" height="100" rx="10" fill="#4dabf7" stroke="#1971c2"/>
  <text x="265" y="105" fill="white" font-family="Arial" font-weight="bold">Decoder Block</text>
</svg>
</p>

## Key Characteristics
- **Autoregressive Generation:** One token at a time.
- **Scaling Laws:** Performance improves predictably with more parameters and data.
- **Zero-Shot Learning:** Ability to perform tasks without specific fine-tuning.

## Historical Context
The trend started with **GPT-1 (2018)**, which moved away from the then-standard Encoder-Decoder (LSTM/GRU) architectures to a pure Transformer Decoder. This allowed for better parallelization during training and much larger models.

[Back to README](../README.md)
