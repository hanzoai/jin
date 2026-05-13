# ARCHIVED

This repository is archived as of 2026-05-12 and will no longer accept changes.

## What this repo was

`jin` was intended as Hanzo's unified multimodal AI framework — a joint embedding
space with a diffusion-transformer MoE backbone over text, vision, and audio.
That framework was never built.

What actually shipped here is a self-contained set of research experiments on
Joint Embedding Predictive Architectures (JEPAs):

- `jepa/jepa.py` — I-JEPA (ViT + energy-transformer variants)
- `jepa/saccade.py` — Saccade JEPA (own variant; ConvNext teacher/student + MLP predictor)
- `jepa/masked_autoencoder.py` — MAE with self-distillation
- `jepa/transformer.py`, `jepa/patcher.py`, `jepa/datasets.py`, `jepa/train.py` — supporting code
- `jepa/attention_vis.py`, `jepa/deepdream.py` — visualization tools
- `papers/` — DARPA/Army grant proposals around hierarchical JEPA for edge AI (`jin-tac`)

No tests, no `pyproject.toml`/`setup.py` in tree (the `jin_tac.egg-info/`
directory is a stale build artifact). Last functional commit was on
2026-02-28; no work since.

## Why archived

- No internal consumers — `grep` across `~/work/hanzo/*` finds zero `import jin`
  or `from jin` callers. Cross-references in `papers/defense/` and
  `patents/PATENT-PORTFOLIO.md` cite file paths (`jin/attention/fusion.py`,
  `jin/encoders/`, `jin/streaming/multimodal.py`) that do not exist in this tree.
- The "multimodal framework" scope described in `LLM.md` was aspirational and
  never implemented.
- No successor repo covers the same SSL/JEPA research scope:
  - `hanzo/brain` — knowledge graph runtime (SQLite + MCP), not vision SSL.
  - `hanzo/agent`, `hanzo/agents` — agent SDKs / orchestration, not pretraining.
  - `hanzo/mcp` — Model Context Protocol, not representation learning.
  - `hanzo/candle` — Rust ML primitives, not JEPA pretraining.
- The code is research-grade and not in any production path.

## If you want to resume this line of work

Fork the repo and continue under a new name. The most reusable pieces are:

- `jepa/saccade.py` — the Saccade JEPA variant with prediction + cycle-consistency + VICReg losses.
- `jepa/jepa.py` — clean I-JEPA reference implementation.
- `jepa/attention_vis.py` — Dash-based attention map dashboard.

## History preserved

All git history and tags remain intact. Nothing has been deleted.
