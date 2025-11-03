---
layout: post
title: "From Devices to Algorithms to Hardware: My Neuromorphic Path"
date: 2025-11-02
categories: research
tags: [neuromorphic, RRAM, SNN, Loihi, SPICE]
description: "Device-level realities shaping algorithms and verified in hardware."
---

When I think about my work, the pattern is simple: **start from the device, make the algorithm honest, and prove it in hardware**. That’s the thread that runs from my master’s at IIT Delhi with **Prof. Manan Suri** through my Ph.D. at UC Santa Barbara in the **Strukov Research Group** with **Prof. Dmitri Strukov**.

I began on the Python side—writing SNN/CNN training code and, out of curiosity, injecting the messy parts of real non-volatile memories into the loop: quantization, drift, IR-drop, device-to-device variability. The more I modeled non-idealities, the more obvious it became that algorithms could be **better** if they were designed around the physics instead of ignoring it. That thinking led to adaptive neuron models for recurrent spiking networks (see the DEXAT work in *Nature Communications* 2021: <https://www.nature.com/articles/s41467-021-24427-8>) and a practical pipeline on **Intel Loihi** for EMG gesture recognition (arXiv 2022: <https://arxiv.org/abs/2206.02061>).

Around the same time, I explored **near-sensor computing**—using the characteristics of RRAM devices to do a simple contrast-enhancement step close to the sensor for low-light images—and I played with event-based vision, proposing **H2RP**, a lightweight region-proposal idea for event cameras where the background is static (*ICONS 2021*: <https://dl.acm.org/doi/10.1145/3477145.3477263>). None of these were “big fancy models,” but they were fast, transparent, and useful.

At UCSB, I felt I needed to tighten the bottom of the stack—**SPICE-level** understanding—not just empirical fitting. So I built **SpiceXpanse**, an automation framework that orchestrates parameter exploration, parallel HSPICE runs, and composite losses to make RRAM calibration reproducible and scalable (code/paper link forthcoming on my site). That tooling mindset—**make it repeatable, then make it better**—has been crucial.

On the hardware side, I mapped **qCLIF neurons** into a digital flow—**RTL to layout** in 45 nm—so I could see the implications of neuron design on area/timing and run system-level sims with realistic constraints (arXiv 2024: <https://arxiv.org/abs/2404.18066>). It’s not a tape-out (yet), but it closed the loop between model and implementation, which is the point.

Variability is the elephant in the room for memristive devices, so we explored **shadow-memory** compensation: a straightforward way to **reduce programming steps and tighten device distributions** (IMW 2025: <https://tugraz.elsevierpure.com/en/publications/controlling-rerams-switching-characteristics-with-shadow-memory-f>). I implemented and evaluated it in circuit and learning experiments—again, simple idea, measurable gains.

Along the way I co-authored a **wafer-scale passive crossbar** study—my slice was helping a bit in device characterization and SPICE/NN simulations (*Nature Communications* 2025: <https://www.nature.com/articles/s41467-025-63831-2>). And on the algorithmic side, we examined **neoHebbian** synapses with two state variables—conductance plus a thermal/eligibility component—evaluated on RSNN/RL tasks with non-idealities (arXiv 2024: <https://arxiv.org/abs/2411.18272>).

If there’s a philosophy behind all this, it’s three rules:

1) **Start from reality.** Model the device honestly—warts and all.  
2) **Adapt the algorithm.** Don’t force abstraction on the physics; nudge the learning to fit the substrate.  
3) **Prove it in hardware.** Loihi, FPGA, or RTL/layout—something you can poke and measure.

Today I’m extending characterization beyond RRAM (including **eFlash**) and pushing toward reusable, **device-aware spiking IP** that can sit comfortably in a modern SoC. I’m also packaging the tools so others can reproduce and build on top.

— **Sai**

Advisors: **Prof. Dmitri Strukov** (UCSB) · **Prof. Manan Suri** (IIT Delhi)  
Scholar: <https://scholar.google.com/citations?user=FTYIH9wAAAAJ> · GitHub: <https://github.com/saibez> · LinkedIn: <https://www.linkedin.com/in/saisukruth-bezugam>
