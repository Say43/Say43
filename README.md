# Frederic

**Munich, Germany**

I build machine-learning systems from the ground up and measure whether they
actually work.

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

## How I work

**Change one variable at a time.** A result without a control run is an
anecdote. GPT-light's optimizer comparison holds architecture, data, and step
count fixed so the difference means something.

**Treat constraints as a design input.** A free GPU quota that resets weekly
and cuts sessions off mid-run is a real engineering constraint. It drove the
checkpoint-and-resume design, the choice of learning-rate schedule, and the
memory tuning — not the other way around.

**Write down what went wrong.** The mistakes that cost the most were the silent
ones: a data loader that picked up the wrong dataset, a scaler state that
wasn't saved, a GPU that quietly fell back to CPU. They are documented because
they were expensive to find and are the most useful part to read.

**Report the number that is true.** Where results fall short of production
models, the repositories say so and explain why.
