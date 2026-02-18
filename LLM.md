# Jin

Multimodal language model framework using joint embedding space with diffusion transformer MoE architecture. All modalities (text, vision, audio) project to the same embedding dimension.

- **Repo**: https://github.com/hanzoai/jin

## Stack

- Python 3.8+, PyTorch
- einops, torchvision
- Package name: `jin-tac`

## Architecture

### Joint Embedding Space

All modalities map to the same embedding dimension (default 768):

```python
text_embeddings = text_encoder(text)       # -> [B, N, 768]
vision_embeddings = vision_encoder(images)  # -> [B, N, 768]
audio_embeddings = audio_encoder(audio)     # -> [B, N, 768]
```

### Core Components

- **Diffusion Transformer**: Generation quality of diffusion + efficiency of transformers
- **Mixture of Experts (MoE)**: 2 experts active per token out of 8, sparse activation
- **Joint Embedding Space**: Shared token space across modalities

## Directory Structure

```
jin/
├── jepa/                    # Core model code
│   ├── jepa.py              # Base JEPA implementation
│   ├── transformer.py       # Transformer blocks
│   ├── datasets.py          # Data loading
│   ├── train.py             # Training loop
│   ├── saccade.py           # Saccade attention
│   ├── masked_autoencoder.py # MAE implementation
│   ├── deepdream.py         # Deep dream visualization
│   ├── attention_vis.py     # Attention visualization
│   ├── patcher.py           # Patch embedding
│   └── utils.py             # Utilities
├── config/
│   └── training.yml         # Training configuration
├── papers/                  # Research papers and proposals
├── images/                  # Architecture diagrams
└── LLM.md                  # This file
```

## Key Files

| File | Purpose |
|------|---------|
| `jepa/jepa.py` | Base JEPA self-supervised learning |
| `jepa/transformer.py` | Transformer blocks and attention |
| `jepa/train.py` | Training loop |
| `jepa/saccade.py` | Saccade-based attention mechanism |
| `jepa/masked_autoencoder.py` | Masked autoencoder for pre-training |
| `config/training.yml` | Training hyperparameters |

## Rules

- ALWAYS update LLM.md with significant discoveries
- NEVER commit symlinked files (CLAUDE.md, etc.) — gitignored
- NEVER create random summary files — update THIS file
