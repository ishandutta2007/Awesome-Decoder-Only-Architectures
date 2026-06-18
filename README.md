# Awesome-Decoder-Only-Architectures
## Decoder-Only Architectures in AI

Unlike Encoder-Decoder frameworks that map an explicit input space to an output space via a bottleneck, **Decoder-Only architectures** process data sequentially using a single autoregressive pipeline. They predict the next token in a sequence based solely on the context of preceding tokens, making them highly scalable and efficient for generative tasks.

---

## Architectural Overview & Key Implementations

| Category | Key Models | Year | First Paper | Detailed Info | Mechanism | Impact |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Large Language Models (LLMs)** | GPT Series, Llama Series | 2018 | [Improving Language Understanding](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf) | [Read More](./docs/llm.md) | **Causal Masked Self-Attention**: Stacked layers predict the next token by attending only to previous context. | Popularized "scaling laws," proving that massive data and compute yield emergent reasoning. |
| **Code Generation Models** | StarCoder, CodeLlama | 2022 | [Efficient Training of Language Models to Fill in the Middle](https://arxiv.org/abs/2207.14255) | [Read More](./docs/code-gen.md) | **Fill-in-the-Middle (FIM)**: Training on rearranged data to predict text between a known prefix and suffix. | Transformed dev workflows with smart IDE autocompletion and accurate code infilling. |
| **Autoregressive Vision Models** | ImageGPT (iGPT), Parti | 2020 | [Generative Pretraining from Pixels](https://cdn.openai.com/papers/Generative_Pretraining_from_Pixels.pdf) | [Read More](./docs/vision.md) | **Pixel-by-Pixel Flattening**: Images are treated as flattened sequences of visual tokens for sequential generation. | Proved generative principles transfer from text to visual learning without 2D-specific priors. |
| **Multimodal Native Decoders** | Gemini, GPT-4o, Gato | 2022 | [A Generalist Agent (Gato)](https://arxiv.org/abs/2205.06175) | [Read More](./docs/multimodal.md) | **Any-to-Any Tokenization**: A single unified decoder processes text, audio, and visual patches in a shared space. | Drastically reduces latency and retains emotional nuances in multimodal output. |

---

