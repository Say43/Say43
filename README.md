# Frederic

**Munich, Germany**

I build machine-learning, simulation and control projects end to end, almost
entirely on free cloud GPUs (Kaggle and Colab T4s). Each project starts from a
concrete question, runs under a fixed compute budget, and ends with a written
report: what was measured, what held up, what did not, and what is still open.
Failed runs and negative results are documented next to the successful ones.

---

## Research projects

### [PINN](https://github.com/Say43/PINN)

*Graph backbones in physics-informed neural networks*

A preregistered study of whether PDE-structured graph neural ODEs (GRAND,
GREAD) help physics-informed networks escape the failure modes reported in the
PINN literature. The protocol was hash-locked before the first study run, and
numerical precision and regularisation were controlled as separate factors.

- **Result:** at the collapse edge of the reaction equation (60 runs), GREAD
  succeeded in 18 of 20 runs, GRAND in 15 and the MLP baseline in 8. The
  advantage held in all four precision × regularisation strata.
- **Finding:** most failures satisfy the PDE at the collocation points and are
  still wrong between them, so a small training loss was no evidence of a
  correct solution. The graph backbones mainly avoid this failure mode.
- **Open:** the predicted mechanism did not hold, and the comparison matches
  iterations, not compute. A graph run costs 10–16× an MLP run.

### [World-Model](https://github.com/Say43/World-Model)

*nanoWM, a pose-conditioned world model*

A 40M-parameter causal Diffusion Transformer that predicts future video frames
of a 3D scene from past frames and a camera trajectory, trained under a fixed
budget of 20 GPU-hours on procedurally generated rooms.

- **Result:** 37.0 dB PSNR on training scenes and 21.2 dB on unseen rooms,
  against an autoencoder ceiling of 46.0 dB. Camera motion and room layout
  generalise; objects outside the context frames are hallucinated.
- **Method:** the training recipe was chosen by a paired, equal-compute
  ablation. Representation alignment (REPA) lowered the flow loss by about 7 %
  with the same sign in both seeds.
- **Open:** long-horizon rollouts have not been evaluated, and the optimiser
  comparison used an untuned AdamW baseline.

---

## Engineering projects

### [Rocketlanding_MPC](https://github.com/Say43/Rocketlanding_MPC)

*Rocket landing guidance via convex MPC*

A 3-DOF simulation of powered-descent guidance for a reusable booster, written
from scratch. A G-FOLD-style convex program is flown once open-loop and once as
a model predictive controller. It is then chained into a full return profile
that starts from the real separation state of a Falcon 9 mission.

- **Result:** under the same wind gust, open-loop playback missed the pad by
  175 m and the MPC by 1 mm, for 0.5 % more propellant.
- **Validation:** the drag model was checked against public CRS-11 and CRS-12
  telemetry, including a leave-one-flight-out fit. The full profile reaches
  every flight milestone about 2 % early.
- Comes with an interactive, dependency-free 3D web visualisation of the
  return flight.

### [Autonomous-Driving-Stack](https://github.com/Say43/Autonomous-Driving-Stack)

*Alpamayo-1.5 in CARLA*

NVIDIA's 10B-parameter vision-language-action model as the planner of a CARLA
ego vehicle, on a laptop with a 6 GB GPU. Inference runs in 4-bit on two free
Kaggle T4s and is linked to the simulator through a file queue on Hugging Face.
The closed loop runs about 40× slower than real time.

- **Result:** the model reads traffic lights and keeps distance to moving
  vehicles. It reproducibly overestimates the gap to stopped vehicles, and
  twice its trajectory contradicted its own reasoning text.
- **Safety:** an emergency brake and a footprint supervisor are counted
  separately, so a safe run is never reported as an unassisted model success.
- **Scope:** one map, one seed. The runs are case studies, not a benchmark.

### [GPT-light](https://github.com/Say43/GPT-light)

*A language model built from scratch*

A 97M-parameter GPT written directly in PyTorch, with its own tokenizer, and
trained from random initialisation on about 1B tokens of FineWeb-Edu, followed
by chat fine-tuning.

- **Result:** clearly above chance on ARC-Easy (43 %), HellaSwag (39 %) and
  LAMBADA. It stays at chance on ARC-Challenge.
- Muon plus QK-norm gave consistently lower pretraining loss than AdamW alone.
  This comparison changes two variables at once and uses one seed per
  configuration.
- The report lists the bugs that cost GPU quota, including a dataset mix-up
  that had made an earlier result look better than it was.

---

## Smaller studies

**[Finance-ETF-Forecasting](https://github.com/Say43/Finance-ETF-Forecasting):**
I fine-tuned the Kronos foundation model on ETFs, calibrated it with conformal
intervals and tested it walk-forward. Its directional forecasts were
indistinguishable from a random walk, and its volatility forecasts were roughly
on par with GARCH. A model-free trend and volatility-targeting rule improved a
10-ETF portfolio from Sharpe 0.76 to 0.99.

**[TurbofanRUL-NCMAPSS](https://github.com/Say43/TurbofanRUL-NCMAPSS):**
Remaining-useful-life prediction for aircraft engines on NASA's DS02 flight
data. The project compares NGBoost with cross-conformal intervals against a
1D-CNN deep ensemble. NGBoost reached a test RMSE of 10.7 cycles on the
official test set, which includes two flight classes absent from training. A
leaked health-state feature was found and removed before the final numbers.

**[AgentLight](https://github.com/Say43/AgentLight):**
A four-phase QLoRA pipeline (reasoning SFT, repair SFT, replay and GRPO with
unit-test rewards) plus a ReAct execute-and-repair loop for Llama 3.2 3B, run
end to end on one Kaggle T4. The goal was a working architecture. A held-out
HumanEval comparison was not run, so no improvement over the base model is
claimed.

---

