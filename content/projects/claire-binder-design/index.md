---
title: Reproduction of the CLAIRE de novo protein-binder design pipeline
date: 2026-09-01

links:
  - type: code
    url: https://github.com/Milky-mu/CLAIRE

tags:
  - Computational
  - Protein Design
  - Rosetta
  - ProteinMPNN
  - AlphaFold2
---

**A computational project** — independent work alongside my wet-lab dissertation.
I reproduced the CLAIRE small-molecule binder-design pipeline end-to-end, then
pushed it onto two targets it had never been run on.

<!--more-->

<svg viewBox="0 0 900 190" role="img" aria-label="The CLAIRE pipeline: a target ligand passes through Rosetta motif matching, ProteinMPNN sequence design and AlphaFold2 validation to produce binder candidates" style="width:100%;height:auto;margin:2rem 0;color:inherit">
  <defs>
    <marker id="ar" markerWidth="9" markerHeight="9" refX="8" refY="4.5" orient="auto">
      <path d="M0,1 L8,4.5 L0,8" fill="none" stroke="currentColor" stroke-width="1.4" opacity=".55"/>
    </marker>
  </defs>
  <g font-family="ui-sans-serif,system-ui,sans-serif" text-anchor="middle">
    <g opacity=".9">
      <rect x="4" y="44" width="150" height="76" rx="10" fill="currentColor" fill-opacity=".05" stroke="currentColor" stroke-opacity=".28"/>
      <text x="79" y="72" font-size="14" font-weight="600" fill="currentColor">Target ligand</text>
      <text x="79" y="92" font-size="11.5" fill="currentColor" opacity=".7">progesterone</text>
      <text x="79" y="107" font-size="11.5" fill="currentColor" opacity=".7">thalidomide · 4-OHT</text>
    </g>
    <line x1="160" y1="82" x2="196" y2="82" stroke="currentColor" stroke-width="1.4" opacity=".55" marker-end="url(#ar)"/>
    <g>
      <rect x="202" y="44" width="160" height="76" rx="10" fill="currentColor" fill-opacity=".05" stroke="currentColor" stroke-opacity=".28"/>
      <text x="282" y="72" font-size="14" font-weight="600" fill="currentColor">Rosetta</text>
      <text x="282" y="92" font-size="11.5" fill="currentColor" opacity=".7">motif generation</text>
      <text x="282" y="107" font-size="11.5" fill="currentColor" opacity=".7">and matching</text>
    </g>
    <line x1="368" y1="82" x2="404" y2="82" stroke="currentColor" stroke-width="1.4" opacity=".55" marker-end="url(#ar)"/>
    <g>
      <rect x="410" y="44" width="160" height="76" rx="10" fill="currentColor" fill-opacity=".05" stroke="currentColor" stroke-opacity=".28"/>
      <text x="490" y="72" font-size="14" font-weight="600" fill="currentColor">ProteinMPNN</text>
      <text x="490" y="92" font-size="11.5" fill="currentColor" opacity=".7">sequence design</text>
    </g>
    <line x1="576" y1="82" x2="612" y2="82" stroke="currentColor" stroke-width="1.4" opacity=".55" marker-end="url(#ar)"/>
    <g>
      <rect x="618" y="44" width="160" height="76" rx="10" fill="currentColor" fill-opacity=".05" stroke="currentColor" stroke-opacity=".28"/>
      <text x="698" y="72" font-size="14" font-weight="600" fill="currentColor">AlphaFold2</text>
      <text x="698" y="92" font-size="11.5" fill="currentColor" opacity=".7">self-consistency</text>
      <text x="698" y="107" font-size="11.5" fill="currentColor" opacity=".7">validation</text>
    </g>
    <line x1="784" y1="82" x2="820" y2="82" stroke="currentColor" stroke-width="1.4" opacity=".55" marker-end="url(#ar)"/>
    <text x="862" y="78" font-size="12.5" font-weight="600" fill="currentColor">binder</text>
    <text x="862" y="95" font-size="12.5" font-weight="600" fill="currentColor">candidates</text>
    <text x="450" y="22" font-size="11.5" fill="currentColor" opacity=".55">environment built from scratch — Rosetta · PyRosetta · ColabFold</text>
    <text x="450" y="166" font-size="11.5" fill="currentColor" opacity=".55">a latent file-naming defect in the original codebase found and fixed here</text>
    <line x1="282" y1="140" x2="282" y2="152" stroke="currentColor" stroke-width="1.2" opacity=".35"/>
    <line x1="282" y1="152" x2="450" y2="152" stroke="currentColor" stroke-width="1.2" opacity=".35"/>
  </g>
</svg>

## Three targets, not one

| Target | Why this one |
|---|---|
| Progesterone | the repository's built-in example — a correctness baseline |
| Thalidomide | generalization test |
| 4-Hydroxytamoxifen (4-OHT) | generalization test |

The latter two were chosen deliberately: their polar-handle configurations are
chemically distinct enough to probe generalization rather than repeat a known
result.

**All three produced AlphaFold2-self-consistent candidates — best case pLDDT 94.1
at 0.62 Å RMSD.**

## Why it matters to my own work

My dissertation designs bioPROTACs, which need a binding domain against their
target — so the binder is the limiting reagent, and borrowing one confines you to
targets somebody has already solved. Designing binders directly is how that
constraint comes off.

## Related: testing the generalizability of a multistate design method on KRAS

I extracted the computational recipe of **Guo et al. (Science, 2025)** from the
primary literature and built a three-layer framework to test whether it transfers
to the Ras superfamily:

- **Calibration** — T35S, a known state-switching mutant: does the diagnostic
  detect what it claims to?
- **Clinical noise** — G12D, G12C: does it fire on any substitution?
- **Application** — the hypervariable-region mutation from my own dissertation.

The first two layers are what make the third worth believing. This also meant
rebuilding the simulation system in AMBER after diagnosing that a prior model was
nucleotide-free — the replacement is GppNHp- and Mg²⁺-bound, with de novo
parameterization for the ligand and the farnesylated cysteine anchor.

## Toolchain

Rosetta/PyRosetta · ProteinMPNN · AlphaFold2/ColabFold · GROMACS · AMBER/AmberTools
· OpenMM · CHARMM-GUI · antechamber, AM1-BCC, GAFF2 · Python · Linux and cloud GPU
