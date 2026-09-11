# Prothynesis

### MoMMs LLM — runs locally on your computer

Prothynesis is a **Mix of Many Models (MoMMs)** language model system built around a large population of **independently trained reasoning models** instead of a conventional single-model or standard MoE architecture.

## Model Versions

| Model Version                        | Status         | Solver Models | Pool Parameters |
| ------------------------------------ | -------------- | ------------: | --------------: |
| **Prothynensis Mini 1.0 (TestV)**    | Experimental   |         5,120 |       **~395B** |
| **Prothynensis Mini 3.0**            | Unreleased     |        10,240 |       **~790B** |
| **Prothynensis Pro 1.0 (TestV)**     | Experimental   |        10,040 |       **~775B** |
| **Prothynensis Pro 3.0**             | Unreleased     |        20,080 |      **~1.55T** |
| **Prothynensis Ultra 1.0 (TestV)**   | Experimental   |        16,420 |      **~1.27T** |
| **Prothynensis Ultra 3.0**           | Unreleased     |        32,840 |      **~2.53T** |
| **Prothynensis Trinity 1.0 (TestV)** | Experimental   |        24,400 |      **~1.88T** |
| **Prothynensis Trinity 3.0**         | Unreleased     |        48,800 |      **~3.77T** |
| **Prothynensis Trinity 3.1a**        | In Development |       97,600* |     **~7.53T*** |

*Assuming Trinity 3.1a uses the current ~77.16M-parameter solver architecture and 2× the Trinity 3.0 solver population.

> **Pool parameters** are the total parameters across the entire model population. They are not equivalent to the parameters of one dense model.

---

# MoMMs Architecture

Prothynesis uses a **Hierarchical Collaborative Stateful MoMMs architecture**.

Instead of having one large model with internal expert layers, Prothynesis is composed of many **independent models** that can reason, remember, communicate, critique, verify, and synthesize with each other.

### Basic Structure

```text
                         USER
                           │
                           ▼
                    ULTIMATE ORCHESTRAL
                           │
                ┌──────────┼──────────┐
                ▼          ▼          ▼
             MASTER      MASTER      MASTER
                │          │          │
              CHIEF      CHIEF      CHIEF
                │          │          │
           ORCHESTRAL  ORCHESTRAL  ORCHESTRAL
                │          │          │
                └──────────┼──────────┘
                           │
                    DYNAMIC RECRUITMENT
                           │
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
       SOLVER A          SOLVER B         SOLVER C
         ~77M              ~77M             ~77M
          │                  │                │
          └────────── PEER COLLABORATION ────┘
                           │
               ┌───────────┼───────────┐
               ▼           ▼           ▼
            CRITIQUE    EVIDENCE    VERIFICATION
               │           │           │
               └───────────┼───────────┘
                           ▼
                       REVISION
                           │
                        SYNTHESIS
                           │
                           ▼
                         RESULT
```

## Independent Solver Models

Each solver is a real independently trained model.

Every solver has:

* broad knowledge
* reasoning capability
* task state
* working memory
* episodic memory
* peer memory
* verification capability
* collaboration capability

The current solver architecture contains approximately:

**77.16M parameters per model.**

---

## Universal Shared Core + Unique Experience

All solver models are trained on the same overall knowledge universe, but they do **not** receive identical training data.

The default training strategy is approximately:

```text
~1% Universal Shared Core
+
~99% Unique Experience
```

### Universal Shared Core

The Shared Core gives every model a common foundation:

* language understanding
* general knowledge
* reasoning fundamentals
* mathematics fundamentals
* task understanding
* evidence and confidence
* critique and verification
* collaboration concepts
* memory/task concepts

This allows independently trained models to understand each other.

### Unique Experience

The remaining training data is distributed between models with **no intentional duplicate training instances** in the default population.

The allocation is stratified across:

```text
Domain
Difficulty
Task Type
Language
Quality
Source
```

Therefore:

```text
Model A
→ knows broadly
→ deep in systems/code

Model B
→ knows broadly
→ deep in mathematics

Model C
→ knows broadly
→ deep in science/verification
```

They are not isolated specialists. They share broad knowledge while developing different learned experience and priors.

---

# Stateful Models

Every model has its own runtime state.

### Memory

```text
Working Memory
Task Memory
Episodic Memory
Peer Memory
Long-Term Memory
```

### Task State

Models can track:

```text
Objective
Constraints
Subtasks
Hypotheses
Evidence
Candidates
Unresolved Issues
Confidence
Verification State
```

Memory and task state are isolated by task/session to prevent cross-task contamination.

---

# Peer Collaboration

Models are not limited to:

```text
input → answer
```

Instead, they can:

```text
reason
→ publish candidate
→ read peer candidate
→ critique
→ exchange evidence
→ update memory
→ revise
→ verify
→ synthesize
```

Example:

```text
Solver A → Candidate X
Solver B → Candidate Y
Solver C → Critique X
Solver D → Counterexample
Solver E → Verification
        ↓
A/B revise
        ↓
Collaborative synthesis
```

Consensus is **not** simple majority voting.

The system evaluates:

* evidence quality
* reasoning quality
* verification
* consistency
* contradiction
* model reliability
* confidence
* independent agreement

---

# Hierarchical Orchestration

Prothynesis uses multiple levels of orchestral models.

### Orchestral

Handles:

* task decomposition
* solver recruitment
* candidate collection
* initial critique
* verification requests

### Chief Orchestral

Handles:

* cross-orchestral comparison
* conflict detection
* branch coordination
* additional recruitment

### Master Orchestral

Handles:

* major reasoning branches
* conflict resolution
* compute allocation
* high-level verification

### Ultimate Orchestral

Handles:

* global task understanding
* global coordination
* final verification
* stopping decisions
* final synthesis

All orchestral models are themselves stateful collaborative models.

---

# Dynamic Compute

Prothynesis does not require the entire model population for every prompt.

The system can dynamically recruit:

```text
1–3 models
3–10 models
10–30 models
30–100 models
100–1,000+ models
```

depending on:

* task difficulty
* uncertainty
* disagreement
* verification needs
* compute budget
* latency budget

For extreme tasks, the system can theoretically recruit the entire available model pool.

---

# Pure-Token Activation

Pool parameters and active computation are separate concepts.

For the current ~77.16M solver architecture:

```text
1 active solver
≈ 77.16M parameters

100 active solvers
≈ 7.72B parameters

1,000 active solvers
≈ 77.16B parameters

10,000 active solvers
≈ 771.6B parameters

48,800 active solvers
≈ 3.765T parameters
```

The actual number of active parameters depends on how many models are recruited for the current task.

---

# Self-Evaluating Training

Each solver supports multi-run training.

The training system can:

```text
Train
→ Validate
→ Evaluate capabilities
→ Save checkpoint
→ Restart from scratch
→ Train again
→ Compare runs
→ Keep the strongest result
```

Selection uses more than training loss:

```text
Validation
Reasoning
Knowledge
Verification
Generalization
Stability
Overfitting
```

---

# Population Evolution

Prothynesis can evolve the population across generations.

```text
Generation N
      ↓
Benchmark
      ↓
Failure analysis
      ↓
Hard-example mining
      ↓
Curriculum update
      ↓
Teacher distillation
      ↓
Self-play
      ↓
Retraining
      ↓
Generation N+1
```

This allows the model population to improve rather than remaining static.

---

# Trinity 3.x

Trinity is the largest Prothynesis family.

### Trinity 1.0

```text
24,400 solver models
~1.88T solver parameters

10 Orchestral
5 Chief
3 Master
1 Ultimate
```

### Trinity 3.0

```text
48,800 solver models
~3.77T solver parameters

150 Orchestral
75 Chief
45 Master
15 Ultimate
```

Trinity 3.0 is designed to provide:

```text
2× solver population
2× raw solver capacity
15× orchestral hierarchy
stronger collaboration
stronger memory
stronger verification
better orchestration
```

### Trinity 3.1a

Current development target:

```text
~7.6T pool parameters
```

The exact architecture and model population are subject to development changes.

---

# Design Goal

Prothynesis is designed around:

```text
Many Independent Models
        +
Shared Foundation
        +
Unique Experience
        +
Memory
        +
Task State
        +
Peer Collaboration
        +
Verification
        +
Hierarchical Orchestration
        +
Adaptive Compute
        +
Population Evolution
```

The goal is not simply to create a huge parameter count.

The goal is to create a **large population of independent reasoning models that can collectively produce better results than any individual model alone.**
