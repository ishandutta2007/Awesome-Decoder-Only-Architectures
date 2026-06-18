# Autoregressive Vision Models

Autoregressive vision models treat images as sequences of tokens, similar to how LLMs treat text. This allows the powerful transformer decoder architecture to be applied directly to visual data.

## Core Mechanism: Pixel-by-Pixel / Patch-by-Patch Flattening

An image is typically a 3D tensor (Width x Height x RGB). To process it with a decoder, it must be flattened into a 1D sequence. **ImageGPT (iGPT)** flattens pixels, while more modern models like **Parti** use discrete tokens from a VQ-GAN or similar visual tokenizer.

### Diagram: Visual Tokenization
<p align="center">
<svg width="400" height="250" xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="#fff4e6"/>
  
  <!-- Image Grid -->
  <rect x="50" y="50" width="120" height="120" fill="white" stroke="#333"/>
  <line x1="50" y1="90" x2="170" y2="90" stroke="#ccc"/>
  <line x1="50" y1="130" x2="170" y2="130" stroke="#ccc"/>
  <line x1="90" y1="50" x2="90" y2="170" stroke="#ccc"/>
  <line x1="130" y1="50" x2="130" y2="170" stroke="#ccc"/>
  
  <!-- Patches -->
  <rect x="55" y="55" width="30" height="30" fill="#fcc419"/>
  <rect x="95" y="55" width="30" height="30" fill="#fab005"/>
  <rect x="135" y="55" width="30" height="30" fill="#f59f00"/>
  
  <text x="180" y="115" font-family="Arial" font-size="20">➔</text>
  
  <!-- Sequence -->
  <rect x="220" y="55" width="30" height="30" fill="#fcc419"/>
  <rect x="255" y="55" width="30" height="30" fill="#fab005"/>
  <rect x="290" y="55" width="30" height="30" fill="#f59f00"/>
  <text x="330" y="75" font-family="Arial" font-size="14">...</text>
  
  <text x="50" y="30" font-family="Arial" font-size="14" font-weight="bold">2D Image Grid</text>
  <text x="220" y="30" font-family="Arial" font-size="14" font-weight="bold">1D Sequence</text>
  
  <rect x="220" y="150" width="150" height="60" rx="10" fill="#ff922b" stroke="#d9480f"/>
  <text x="245" y="185" fill="white" font-family="Arial" font-weight="bold">Transformer</text>
</svg>
</p>

## Key Characteristics
- **Generative Capability:** Can complete partial images or generate from scratch.
- **Unified Training:** The same loss function (Cross-Entropy) works for both text and pixels.
- **High Resolution Challenges:** Flattening high-res images leads to extremely long sequences.

## Historical Context
**ImageGPT (2020)** proved that generative pre-training on pixels yields excellent visual features, even without the hierarchical bias of CNNs.

[Back to README](../README.md)
