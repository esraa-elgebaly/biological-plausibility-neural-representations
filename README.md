# biological-plausibility-neural-representations
Comparing vanilla RNNs, Dale-constrained RNNs, and spiking neural networks on a context-dependent cognitive task.
# Does Biological Plausibility Shape Neural Representations?

### Comparing Vanilla RNNs, Dale's-Law-Constrained RNNs, and Spiking Neural Networks on a Context-Dependent Cognitive Task

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)]()
[![Status](https://img.shields.io/badge/status-in%20progress-orange.svg)]()

## Overview

How much does biological plausibility matter for the way neural networks represent information?

Artificial recurrent neural networks (RNNs) can reproduce complex cognitive
behaviors and have been used as computational models of cortical dynamics.
However, conventional RNNs abstract away several properties of biological
neural circuits, including spiking activity and the separation of excitatory
and inhibitory neurons implied by Dale's law.

This project investigates whether introducing these biological constraints
changes the internal computations and representational geometry learned by
neural networks.

We compare three architectures trained on the same context-dependent
two-alternative forced-choice (2AFC) task under matched training protocols:

1. **Vanilla RNN** — a standard rate-based recurrent neural network.
2. **Dale-RNN** — a recurrent network constrained by Dale's law, separating
   excitatory and inhibitory populations.
3. **SNN** — a spiking neural network implementing discrete neuronal dynamics.

Because all three models perform the same task, the comparison allows us to
ask whether differences in internal representations arise from biological
constraints rather than differences in task demands.

---

## Research Question

> **Does biological plausibility change the computational representations
> learned by neural networks, even when different architectures achieve
> comparable behavioral performance?**

More specifically, we ask whether Dale's law alone can move the
representational structure of a rate-based RNN toward that of a spiking
network, or whether spiking dynamics introduce additional computational
properties that cannot be recovered by Dale's law alone.

---

## Scientific Motivation

Context-dependent decision-making requires a neural system to use the same
sensory information differently depending on the current task context.

Mante et al. (2013) demonstrated that recurrent network dynamics can reproduce
important aspects of context-dependent selection and integration observed in
prefrontal cortex.

This work provides the starting point for our study.

Rather than asking whether a network can solve the task, we ask a deeper
question:

**Do different neural architectures solve the task using the same internal
representations and dynamics?**

A standard RNN can achieve high behavioral performance without explicitly
implementing biological constraints. A spiking network, however, operates
through fundamentally different neural dynamics. Dale's law introduces
another constraint by restricting neurons to be consistently excitatory or
inhibitory.

Comparing these architectures provides a way to disentangle different
components of biological plausibility.

---

## Experimental Design

All three architectures are trained on the same context-dependent 2AFC task
using matched training protocols.

### Model 1 — Vanilla RNN

A conventional rate-based recurrent neural network.

This model provides the computational baseline against which the biologically
constrained architectures are evaluated.

### Model 2 — Dale-RNN

A rate-based recurrent neural network constrained by Dale's law.

Neurons are assigned excitatory or inhibitory identities, restricting the
sign of their outgoing synaptic connections.

This model allows us to isolate the effect of connectivity constraints without
introducing spiking dynamics.

### Model 3 — Spiking Neural Network

A spiking recurrent network in which information is represented through
time-varying spike activity.

This architecture introduces temporal spiking dynamics in addition to
biological constraints on neuronal interactions.

---

## Why Three Models?

A simple RNN-vs-SNN comparison would not tell us which biological feature is
responsible for an observed difference.

Our three-model design creates a controlled comparison:

                    Biological constraints
                           │
              ┌────────────┴────────────┐
              │                         │
          Dale's law              Spiking dynamics
              │                         │
          Dale-RNN                     SNN
              │                         │
              └──────────┬──────────────┘
                         │
                    Vanilla RNN
                       baseline

This allows us to ask:

- What changes when Dale's law is introduced?
- What changes when spiking dynamics are introduced?
- Which representational properties are shared across architectures?
- Which properties are specific to spiking networks?

---

## Research Questions

### RQ1 — Representational similarity

**Do the three architectures develop similar internal representations despite
having different neural dynamics?**

We compare population-level representations across the course of a trial
rather than examining a single time point.

---

### RQ2 — Contribution of biological constraints

**Does Dale's law alone move the representations of a rate-based network
toward those of a spiking network?**

The comparison between Vanilla RNN → Dale-RNN → SNN allows us to separate
connectivity constraints from spiking dynamics.

---

### RQ3 — Task-variable representations

**Do biologically constrained architectures organize information about task
variables differently from a conventional RNN?**

We examine representations associated with:

- context / rule
- sensory stimulus
- decision / choice
- task-relevant versus task-irrelevant information

---

### RQ4 — Temporal organization

**At which stage of the trial do the architectures' representations
converge or diverge?**

Rather than treating representation as a static property, we track
representational similarity over time.

This allows us to investigate whether architectural differences emerge during:

1. rule encoding
2. stimulus processing
3. evidence integration
4. decision formation

---

### RQ5 — Robustness under perturbation

If computational resources permit:

**Does biological constraint confer robustness to perturbations?**

We will investigate how representations and task performance change after
controlled perturbations such as:

- unit shuffling
- connection perturbation
- unit lesioning

This asks whether biological constraints influence not only representation,
but also the robustness of the resulting computation.

---

## Analysis Pipeline

### 1. Behavioral performance

For each architecture we evaluate:

- task accuracy
- learning curves
- condition-specific performance
- error patterns

Performance provides the behavioral baseline.

---

### 2. Population dynamics

We analyze the activity of the full neural population across time.

Depending on the architecture, this includes:

- recurrent hidden states
- firing rates
- spike trains
- population trajectories

---

### 3. Dimensionality reduction

We characterize population geometry using methods such as:

- PCA
- UMAP
- manifold analysis

The goal is to determine how task variables are organized in population
space.

---

### 4. Representational Similarity Analysis

Representational similarity analysis (RSA) is used to compare the internal
organization of task conditions across models.

Rather than comparing individual neurons directly, we compare the structure
of population representations.

For each time point:

    Neural activity
          │
          ▼
    Condition representations
          │
          ▼
    Representational dissimilarity matrix
          │
          ▼
    Cross-model comparison

This allows us to ask not only:

> "Do the networks represent the task similarly?"

but also:

> "When during the trial do their representations become similar or diverge?"

---

### 5. Task-variable decoding

We relate representational geometry to task variables such as:

- context / rule
- stimulus identity
- choice

This distinguishes similarity between networks from the actual information
encoded by those networks.

---

### 6. Dynamical analysis

Where appropriate, we investigate:

- neural trajectories
- fixed points
- attractor-like structure
- dynamical subspaces
- temporal evolution of task representations

These analyses connect representational geometry to the mechanisms used
to solve the task.

---

### 7. Perturbation analysis

As an extension, we test whether different architectures respond differently
to controlled perturbations.

Performance and representation are measured before and after perturbation.

---

## Expected Contribution

The central contribution of this project is not simply comparing whether an
RNN performs better than an SNN.

Instead, we aim to distinguish:

**behavioral equivalence**

from

**computational equivalence.**

Two networks can achieve the same task accuracy while implementing the task
through different internal representations and dynamical mechanisms.

Our three-architecture comparison provides a controlled framework for asking
which aspects of biological plausibility contribute to these differences.

---

## Reproducibility

All models are trained using matched task conditions and training protocols.

The repository will contain:

- model implementations
- training configurations
- trained checkpoints
- analysis scripts
- evaluation procedures
- generated figures
- experiment logs

The goal is to make the comparison reproducible and allow future experiments
to extend the analysis.

---

## Project Structure

```text
biological-plausibility-neural-representations/
│
├── README.md
├── LICENSE
├── requirements.txt
├── pyproject.toml
│
├── configs/
│   ├── vanilla_rnn.yaml
│   ├── dale_rnn.yaml
│   └── snn.yaml
│
├── data/
│   └── README.md
│
├── models/
│   ├── vanilla_rnn.py
│   ├── dale_rnn.py
│   └── snn.py
│
├── training/
│   ├── train_rnn.py
│   ├── train_dale_rnn.py
│   └── train_snn.py
│
├── analysis/
│   ├── representational_similarity.py
│   ├── dimensionality.py
│   ├── trajectory_analysis.py
│   ├── decoding.py
│   └── perturbation.py
│
├── evaluation/
│   ├── behavioral_performance.py
│   └── compare_models.py
│
├── notebooks/
│   ├── 01_task_exploration.ipynb
│   ├── 02_model_comparison.ipynb
│   ├── 03_representational_analysis.ipynb
│   └── 04_perturbation_analysis.ipynb
│
├── checkpoints/
│   └── README.md
│
├── figures/
│   └── README.md
│
└── results/
    └── README.md
