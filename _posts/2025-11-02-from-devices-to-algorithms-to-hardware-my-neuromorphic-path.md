---
layout: post
title: "From Devices to Algorithms to Hardware: My Neuromorphic Path"
date: 2025-11-02
categories: research
tags: [neuromorphic, RRAM, SNN, Loihi, SPICE]
description: "Device-level realities shaping algorithms and verified in hardware."
---

My work sits at the seam between devices, algorithms, and hardware. I try to keep the stack honest: start from what the device actually does, shape the learning around it, and check the claim on something you can probe.

I trained in two places that reward this habit—an M.S. at IIT Delhi with **Prof. Manan Suri** and a Ph.D. at UC Santa Barbara in the **Strukov Research Group** with **Prof. Dmitri Strukov**.

## What I actually did

I began on the software side and pulled hardware effects into the loop: quantization, drift, IR-drop, and device-to-device spread. Designing under those constraints led to adaptive neuron models for recurrent SNNs (DEXAT, *Nature Communications* 2021: <https://www.nature.com/articles/s41467-021-24427-8>) and a practical **Intel Loihi** pipeline for EMG gesture recognition (arXiv 2022: <https://arxiv.org/abs/2206.02061>).

At the edge, I looked at **near-sensor computing** with RRAM for low-light contrast enhancement and worked on event-based vision. I proposed **H2RP**, a lightweight region-proposal method when the background is static (*ICONS 2021*: <https://dl.acm.org/doi/10.1145/3477145.3477263>). Small models, direct paths from sensor to decision.

Tooling matters, so I turned a pile of scripts into **SpiceXpanse**—automation for reproducible RRAM calibration: define sweeps, launch parallel HSPICE runs, use composite losses, and keep the whole configuration in the log (code/paper forthcoming). Calibration here means distributions, seeds, and corners, not a single number.

On the hardware side, I pushed **qCLIF neurons** through a digital flow—**RTL → layout** in 45 nm—to see area/timing/energy truth rather than estimates (arXiv 2024: <https://arxiv.org/abs/2404.18066>). With placed-and-routed results, system-level sims carry constraints you can't hand-wave.

Variability sets the ceiling for memristive systems, so we evaluated **shadow-memory** compensation—pairing cells and scheduling pulses to narrow effective distributions—and measured its impact in circuits and learning loops (IMW 2025: <https://tugraz.elsevierpure.com/en/publications/controlling-rerams-switching-characteristics-with-shadow-memory-f>). The goal was operational: fewer programming steps and tighter spreads.

I also contributed device characterization and SPICE/NN simulations to a **wafer-scale passive crossbar** effort across multiple groups (*Nature Communications* 2025: <https://www.nature.com/articles/s41467-025-63831-2>), and examined **neoHebbian** synapses with two state variables—conductance plus a thermal/eligibility term—on RSNN/RL tasks under non-idealities (arXiv 2024: <https://arxiv.org/abs/2411.18272>).

## Where this is going

In practice I keep three things straight: model devices as they are; design algorithms that don't fight the substrate; validate on hardware you can poke—Loihi, FPGA, or plain RTL/layout.

Next steps: extend characterization beyond RRAM (including **eFlash**), and package **device-aware spiking IP** that drops cleanly into a modern SoC. The parallel track is tooling—make reruns trivial so results are boring to reproduce and easy to build on.

If you work at this device → algorithm → hardware intersection, happy to compare notes.

— **Sai**

Advisors: **Prof. Dmitri Strukov** (UCSB) · **Prof. Manan Suri** (IIT Delhi)
Scholar: <https://scholar.google.com/citations?user=FTYIH9wAAAAJ> · GitHub: <https://github.com/saibez> · LinkedIn: <https://www.linkedin.com/in/saisukruth-bezugam>
