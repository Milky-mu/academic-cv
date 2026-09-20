---
title: Computational protein design and simulation
date: 2026-09-01

links:
  - type: code
    url: https://github.com/Milky-mu

tags:
  - Protein Design
  - Molecular Dynamics
  - Rosetta
  - ProteinMPNN
  - AlphaFold2
  - AMBER
---

The computational half of my work, built independently alongside wet-lab
dissertation research: de novo binder design, tests of whether published design
methods generalize, and membrane-embedded simulation systems constructed from
scratch.

<!--more-->

## Why I built this side of the work

My dissertation designs bioPROTACs — degraders that need a binding domain against
their target. That makes the binding domain the limiting reagent, and borrowing
one constrains you to targets somebody has already solved. Designing binders
directly is how that constraint comes off, so I have been building the capability
deliberately rather than waiting for a collaborator.

The same instinct applies to published methods. A technique demonstrated on the
system it was developed for has not yet been shown to be *general* — and for the
targets I care about, generality is the whole question.

## De novo binder design

I reproduced the **CLAIRE** small-molecule binder-design pipeline end-to-end —
Rosetta motif generation and matching, sequence design with ProteinMPNN, and
AlphaFold2 self-consistency validation — building the full Rosetta / PyRosetta /
ColabFold environment from scratch.

Rather than stopping at the repository's built-in example (progesterone), I ran
it on **thalidomide** and **4-hydroxytamoxifen**, chosen because their polar-handle
configurations are chemically distinct enough to probe generalization instead of
repeating a result. All three yielded AlphaFold2-self-consistent candidates, the
best at **pLDDT 94.1, 0.62 Å RMSD**. I also diagnosed and fixed a latent
file-naming defect in the original codebase, and published the reproduction
openly — including the debugging narrative, which is usually the part omitted.

## Testing whether a design method generalizes

I extracted the computational recipe of **Guo et al. (Science, 2025)** — an
AF2-based conformational-state reversion scan combined with position-tied
ProteinMPNN — from the primary literature, and built a three-layer framework to
test whether it transfers to KRAS and the wider Ras superfamily:

- a **calibration layer** (T35S, a literature-established state-switching mutant),
  confirming the diagnostic detects what it claims to;
- a **clinical-noise layer** (G12D, G12C), checking it does not simply fire on any
  substitution;
- an **application layer** — the hypervariable-region mutation my own dissertation
  identified as driving escape from degradation.

The first two layers are what make the third worth believing.

## Simulation and system building

Much of the above depends on simulation systems being right in the first place.
I run 200-ns all-atom molecular dynamics of farnesylated, membrane-embedded KRAS,
and rebuilt one system in AMBER after diagnosing a structural defect in a prior
model — it was nucleotide-free. The replacement is nucleotide- and Mg²⁺-bound
(GppNHp), which required de novo force-field parameterization for both the
non-standard GppNHp ligand and the farnesylated cysteine membrane anchor.

## Scope

**Design** — Rosetta/PyRosetta, ProteinMPNN, AlphaFold2/ColabFold.
**Simulation** — GROMACS, AMBER/AmberTools, OpenMM, CHARMM-GUI, force-field
parameterization (antechamber, AM1-BCC, GAFF2).
**Omics** — WGS variant calling, DIA mass-spectrometry quantification, ubiquitomic
and proteomic profiling with cross-validated dual search engines.
**Computing** — Python scientific computing, Linux and cloud-GPU environment
setup and orchestration.
