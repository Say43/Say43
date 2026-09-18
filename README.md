# Frederic

**Munich, Germany**

I build machine-learning, forecasting, and control systems from the ground up.
My projects are reproducible experiments, with efficient use of limited compute,
calibrated uncertainty, and with a documentation of negative results as clearly as the
successful ones.

---

## Projects

### [Rocket Landing Guidance via Convex MPC](https://github.com/Say43/Rocketlanding_MPC)

A from-scratch 3-DOF simulation of powered-descent guidance for a reusable
booster. It uses convex optimization both as an open-loop planner and as a
closed-loop model predictive controller, then connects the landing burn to a
full return profile based on public Falcon 9 telemetry.

- G-FOLD-style lossless convexification with successive convexification for
  aerodynamic drag
- Open-loop and MPC guidance compared under wind and state disturbances
- Atmosphere and drag model validated against public CRS-11 and CRS-12
  telemetry
- Self-contained interactive 3D web visualization of the simulated return

### [GPT-light](https://github.com/Say43/GPT-light) — a language model built from scratch

A 97-million-parameter GPT written directly in PyTorch. The architecture,
tokenizer, training loop, and evaluation suite are implemented from first
principles, and the model was trained from random initialization on public
text.

- Modern architecture with RoPE, SwiGLU, RMSNorm, QK-norm, and an independent
  implementation of the Muon optimizer
- Controlled comparison between two full training runs that differ only in
  optimizer and normalization
- Evaluation on ARC-Easy, ARC-Challenge, HellaSwag, and LAMBADA using a
  reimplemented standard log-likelihood protocol
- Results include the failures and data issues discovered along the way

### [Finance ETF Forecasting](https://github.com/Say43/Finance-ETF-Forecasting)

A rigorous investigation of fine-tuning the Kronos financial foundation model
on ETF data, including leakage-free calibration, walk-forward testing, and
follow-up research after the model showed no directional edge.

- Split-conformal prediction intervals and statistical comparison against
  naive, GARCH, and EWMA baselines
- Negative directional result documented instead of optimized away
- Modest volatility-forecasting skill and independent portfolio experiments
  with trend following and volatility targeting
- Reproducible research pipeline plus a local forecast web interface

### [Turbofan RUL — N-CMAPSS](https://github.com/Say43/TurbofanRUL-NCMAPSS)

Predictive maintenance for aircraft engines using NASA's realistic N-CMAPSS
DS02 flight profiles. The project compares classical machine learning and deep
sequence models for remaining-useful-life prediction, with uncertainty rather
than point estimates alone.

- Cycle-level feature engineering and sequence modeling with leakage-safe
  unit-based splits
- Gradient boosting and NGBoost compared with CNN/LSTM approaches
- Quantile, ensemble, and MC-dropout uncertainty estimates
- Evaluation with RMSE, the asymmetric NASA PHM score, interval coverage, and
  calibration

### [AgentLight](https://github.com/Say43/AgentLight) — a coding agent built end to end

A complete training-to-inference pipeline that turns Llama 3.2 3B Instruct into a
working coding agent: reasoning SFT, general-assistant replay, GRPO with unit-test
rewards, and an inference-time ReAct loop that executes generated Python, observes
test failures, and retries.

- Full pipeline run on a single Kaggle T4 within the 16h budget; final GRPO
  adapter verified and checksummed
- GRPO uses unit-test outcomes as an objective, verifiable reward
- Sandboxed execution is shared by training rewards and the ReAct agent
- Licence-compliant training data only (no closed-model distillation)
- The goal was a functioning architecture, not a benchmark result; a HumanEval
  before/after comparison is deliberately out of scope, so no performance gain
  is claimed
