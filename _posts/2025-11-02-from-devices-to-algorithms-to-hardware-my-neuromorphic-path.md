---
layout: post
title: "From Devices to Algorithms to Hardware: My Neuromorphic Path"
date: 2025-11-02
categories: research
tags: [neuromorphic, RRAM, SNN, Loihi, SPICE]
description: "Device-level realities shaping algorithms and verified in hardware."
---

I’m an ML engineer who wants to build low-power, brain-inspired AI systems (neuromorphic systems). For this, when I think about my work, the pattern is simple: start from the device, make the algorithm honest, and prove it in hardware. That’s the thread that runs from my master’s at IIT Delhi with Prof. Manan Suri through my Ph.D. at UC Santa Barbara in the Strukov Research Group with Prof. Dmitri Strukov.

I began on the ML algorithm side—training SNNs/CNNs—and pushed real-world effects into the loop: **quantization, drift, IR-drop, device-to-device variability** to see when they break (TED, 2020). When we looked closely at **RRAM characterization**, conductance/relaxation is well captured by **double exponentials** (fast + slow components). That insight led to **double-exponential adaptive thresholds—DEXAT**—which in practice delivered **faster, more stable convergence** in recurrent SNNs (*Nature Communications*, 2021). Later, we built a **Loihi** pipeline for real-time EMG gesture recognition (ISCAS 2022) using the same neuron model, explored **near-sensor compute** with RRAM for low-light contrast enhancement (DRC 2023), and proposed **H2RP**, a lightweight region-proposal method for event cameras in static-background scenes (ICONS, 2021). Lean, transparent, useful.

Once at UCSB, I tightened the bottom of the stack. Rather than rely on empirical fits, I built **SpiceXpanse**, an automation framework that makes **RRAM parameter extraction and calibration reproducible**—parameter exploration, **parallel HSPICE**, and **composite loss functions**—so device models become stable inputs to training and benchmarking.

From there, I pushed the ML-to-hardware loop further. I mapped **qCLIF neurons** through a digital flow—**RTL → layout in 45 nm**—to quantify **ML-relevant costs** (area/timing/latency) and to run system-level sims under realistic budgets (NICE, 2024). It’s pre-tapeout, but it **closes the loop** from neuron design to implementation.

Because **variability** dominates memristive systems, we studied **shadow-memory compensation** to reduce programming steps and tighten device distributions—yielding **smoother learning behavior** (IMW, 2025). I also contributed **device characterization and SPICE/NN simulations** to a **wafer-scale passive crossbar** study (*Nature Communications*, 2025), examining robustness under yield limits and line parasitics. On the algorithmic side, we explored **neoHebbian synapses** with two state variables—conductance plus a thermal/eligibility component—evaluated on RSNN/RL tasks **with non-idealities in the loop** (IEDM 2023, arXiv, 2024). Across these projects, the throughline stays ML-centric: datasets, training loops, and learning dynamics shaped by what the physics can actually deliver.

If there’s a philosophy behind my work, it’s three rules:

1. **Start from reality.** Model the device—warts and all.  
2. **Adapt the algorithm.** Tie learning rules to measured behavior; don’t force abstraction on the physics.  
3. **Prove it on silicon.** Loihi/FPGA are stepping stones; the milestone is an **ASIC integrating the target NVM (RRAM/eFlash) or a co-packaged array**, validated with **measured NVM crossbars/arrays** you can probe on the bench.

Today I’m extending characterization beyond RRAM (including **eFlash**) and pushing toward reusable, **device-aware spiking IP** that can sit comfortably in a modern SoC. I’m also packaging the tools so others can reproduce and build on top.

— **Sai Sukruth Bezugam**

Advisors: **Prof. Dmitri Strukov** (UCSB) · **Prof. Manan Suri** (IIT Delhi)  
Scholar: <https://scholar.google.com/citations?user=FTYIH9wAAAAJ> · GitHub: <https://github.com/saibez> · LinkedIn: <https://www.linkedin.com/in/saisukruth-bezugam>
