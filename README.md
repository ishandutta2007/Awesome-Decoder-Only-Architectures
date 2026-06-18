# Awesome-Decoder-Only-Architectures
## Decoder-Only Architectures in AI

Unlike Encoder-Decoder frameworks that map an explicit input space to an output space via a bottleneck, **Decoder-Only architectures** process data sequentially using a single autoregressive pipeline. They predict the next token in a sequence based solely on the context of preceding tokens, making them highly scalable and efficient for generative tasks.

---

## Architectural Overview

| Model Category | Key Examples | Primary Modality & Input/Output | Core Mechanism |
| :--- | :--- | :--- | :--- |
| **Large Language Models (LLMs)** | **GPT-4**, **Llama 3**, **Mistral** | Text → Text (Generation, Chat, Reasoning) | **Causal Masked Self-Attention**: Tokens can only attend to previous tokens in the sequence, preventing leaks from the future. |
| **Code Generation Models** | **CodeLlama**, **StarCoder** | Code/Text → Code (Autocompletion, Synthesis) | **Fill-in-the-Middle (FIM)**: Specialized causal masking that allows the model to condition on both prefix and suffix code block context. |
| **Autoregressive Vision Models** | **ImageGPT**, **Parti** | Pixels/Text → Image / Pixels → Pixels | **Pixel-by-Pixel Flattening**: Images are treated as a flattened sequence of visual tokens and generated sequentially. |
| **Multimodal Native Decoders** | **Gemini**, **GPT-4o** | Text/Image/Audio → Text/Image/Audio | **Any-to-Any Tokenization**: Inputs from all modalities are mapped into a single shared embedding space and processed by one uniform decoder. |

---

## Key Architectures & Implementations

### 1. Large Language Models (The Autoregressive Kings)

#### GPT Series (Generative Pre-trained Transformer) by OpenAI
* **Mechanism:** GPT models stack masked self-attention layers. When given a prompt, the model processes the tokens simultaneously during ingestion (prefill), and then generates new text token-by-token (decoding) by appending each new token back into its own input sequence.
* **Impact:** Popularized the paradigm of "scaling laws," proving that raw parameter count, data volume, and compute yield emergent reasoning capabilities without changing the fundamental architecture.

#### Llama Series by Meta
* **Mechanism:** An open-weights implementation of the standard decoder-only Transformer, introducing key optimizations like Rotary Position Embeddings (RoPE), SwiGLU activation functions, and Grouped-Query Attention (GQA) for faster inference.
* **Impact:** Democratized AI research by providing production-grade, highly efficient decoder models for local deployment and fine-tuning.

### 2. Code Generation (The Context Completers)

#### StarCoder / CodeLlama
* **Mechanism:** While still structurally decoder-only, these models use **Fill-in-the-Middle (FIM)** training. The data array is rearranged to place a middle section of code at the end of the sequence, training the causal model to predict text trapped between a known prefix and suffix.
* **Impact:** Transformed software development by enabling smart IDE autocompletion, code infilling, and accurate docstring generation.

### 3. Autoregressive Vision & Image Generation

#### ImageGPT (iGPT) by OpenAI
* **Mechanism:** This approach flattens images into a single sequence of pixels (or pixel clusters) and trains a standard GPT-2 decoder to predict the next pixel value. 
* **Impact:** Proved that generative pre-training principles transfer perfectly from human language to visual representation learning without any built-in knowledge of 2D image structures.

### 4. Multimodal Native Decoders (The Any-to-Any Systems)

#### Native Omni Models (e.g., GPT-4o, Gemini Ecosystem)
* **Mechanism:** Rather than stitching a separate vision encoder to a text decoder, these modern systems feed text tokens, audio waveforms (tokenized), and visual patches directly into a singular, massively unified decoder network.
* **Impact:** Drastically reduces voice-to-voice latency and retains emotional nuances (tonality, pacing) that are typically lost when routing data through separate encoder pipelines.

