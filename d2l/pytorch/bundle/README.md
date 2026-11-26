# Dive into Deep Learning — pytorch notebooks

These are the executed pytorch notebooks from the book. Computed outputs and the
figures referenced by the notebooks are included. The matching `d2l` source and
pinned environments are included as well.

The latest source is at <https://github.com/smolix/d2l-neu>.

## CPU setup (recommended first)

Install [uv](https://docs.astral.sh/uv/getting-started/installation/), then run:

    uv venv --python 3.12
    uv pip sync pylock.cpu.toml
    uv run --no-sync jupyter lab

The Language Models chapters (`chapter_lm-*`) need Transformers and the OpenAI client
on top of PyTorch: for them use `pylock.lm-cpu.toml` (or `pylock.lm-gpu.toml`)
in a separate venv, e.g. `uv venv --python 3.12 .venv-lm`, then
`VIRTUAL_ENV=.venv-lm uv pip sync pylock.lm-cpu.toml`.

## NVIDIA GPU setup

On Linux/x86-64 with a compatible NVIDIA driver, replace the CPU lock above:

    uv pip sync pylock.gpu.toml
    uv run --no-sync jupyter lab

The GPU lock is framework-specific; check that `nvidia-smi` works before using
it. The notebooks import the backend as, e.g.:

    from d2l import torch as d2l

Notebook outputs can be read offline. Executing notebooks that use datasets or
pretrained models downloads those assets on first use and therefore needs an
internet connection and additional disk space.
