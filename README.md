# Frederic

**Munich, Germany**

I build machine-learning systems from the ground up and try to make them as efficient as possible to not rely on expensive GPU runtimes. I try to implement frontier architectures and techniques to learn as much as possible about the current state of ai-systems.

---

## Projects

### [GPT-light](https://github.com/Say43/GPT-light) — a language model built from scratch

A 97-million-parameter GPT written directly in PyTorch. The architecture, the
training loop, the tokenizer, and the evaluation code are all implemented from
first principles; the weights were trained from random initialization on public
text. Nothing is downloaded and adapted — this is not a fine-tuned existing
model.

- Modern architecture: RoPE, SwiGLU, RMSNorm,
  QK-norm, and a from-scratch implementation of the Muon optimizer
- **A controlled experiment:** two full training runs, identical in every
  respect except the optimizer and normalization, so the measured difference
  can be attributed to that one change
- Scored on ARC, HellaSwag and LAMBADA using the standard log-likelihood
  protocol, reimplemented from scratch
- The failures are documented next to the results — including a silent data
  mix-up that invalidated an entire run

### [AgentLight](https://github.com/Say43/AgentLight) — reinforcement learning on verifiable rewards

A coding agent built by fine-tuning Llama 3.2 3B. The idea that makes it work
on a small budget: the reward signal is **objective**. The model writes Python,
the code is executed against unit tests, and the fraction of tests that pass is
the reward — no human raters, no model-as-judge.

- Pipeline: reasoning-SFT → repair-SFT → general-SFT → GRPO
- An inference-time ReAct loop turns generation into agency: execute, observe
  the failure, revise
- Full licence compliance for a derivative model — Built with Llama

### [unsloth-colab-finetuning](https://github.com/Say43/unsloth-colab-finetuning) — the tooling

The reusable Colab workspace behind the fine-tuning experiments: versioned
notebook, reproducible GitHub-to-Colab sync, datasets kept with the code.

---

