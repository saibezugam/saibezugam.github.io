---
layout: post
title: "From Devices to Algorithms to Hardware: My Neuromorphic Path"
date: 2025-11-02
categories: research
tags: [neuromorphic, RRAM, SNN, Loihi, SPICE]
description: "A device→algorithm→hardware journey: modeling real non-idealities, co-designing learning rules, and validating on silicon."
---

On a humid Delhi evening, a memristor on my probe station refused to behave. The conductance crept, the compliance tripped, and the “clean” Python curve I expected from my notebook didn’t show up on the screen. That mismatch left a permanent mark: **start from the device, adapt the algorithm to reality, and prove it in hardware**. Everything since has been an attempt to stay honest to that sequence.

I carried that mindset from my M.S. at IIT Delhi with **Prof. Manan Suri** to my Ph.D. at UC Santa Barbara in the **Strukov Research Group** with **Prof. Dmitri Strukov**. I began on the software side—training SNN/CNN models, writing utilities, plotting losses—until curiosity pulled the hardware back into the loop. I started injecting what the devices actually do: quantization, drift, IR-drop, device-to-device variability. Once the model had to live under those constraints, we stopped over-fitting to fiction and found rules that were robust to noise and drift. That path led to adaptive neuron models for recurrent SNNs (DEXAT, *Nature Communications* 2021) and later to a practical **Intel Loihi** pipeline for EMG gesture recognition—latencies you can feel, not just read in a table (arXiv 2022).

## From device physics to algorithms
**Design to the substrate.** If RRAM cells saturate or wander, don’t wish it away—shape the learning so it leans into those limits. That idea spilled into **near-sensor computing**: a simple contrast-enhancement step that uses device characteristics to make low-light frames usable. I also worked at the edge of event-based vision with **H2RP**, a lightweight region-proposal method when backgrounds are static (*ICONS 2021*). These weren’t huge models; they used the right inductive bias and a fast path from sensor to decision.

**Make it repeatable, then make it better.** At UCSB I realized my “one-off scripts + manual tuning” didn’t scale. So I built **SpiceXpanse**, an automation framework that standardizes RRAM calibration: define sweeps, launch parallel HSPICE runs, compute composite losses, and log everything so you can rerun it next week and get the same answer. Calibration isn’t a single number—it’s seeds, corners, and candidate models. Turning that into a consistent workflow meant we could compare ideas fairly and move faster without losing rigor.

A small but important side effect of this tooling mindset is cultural: once experiments are trivially reproducible, conversations shift from *whether* a result is real to *how* to improve it. That saves time, especially when multiple groups are touching different parts of the stack.

## Closing the loop in hardware
**From RTL to layout.** Algorithms eventually meet silicon economics. I pushed **qCLIF neurons** through a digital flow—**RTL → layout** in 45 nm—to see how neuron design choices read out in area, timing, and energy. With a placed-and-routed netlist, the system-level simulations stopped being hand-wavy; constraints were explicit, and trade-offs were visible. That closed the loop from an idea in a notebook to a block you can draw in the floorplan (arXiv 2024).

**Taming variability.** Variability is the elephant in any memristive room. We explored **shadow-memory** compensation—pairing cells and scheduling pulses so the effective distributions narrow—then measured the impact in circuits and learning loops (IMW 2025). It’s a straightforward idea, but it cut programming steps and tightened spreads in ways that actually matter when you build a system. The most satisfying part wasn’t the figure in the paper; it was watching the programming algorithm converge faster on stubborn devices while the distributions tightened in real measurements.

## Scaling up and what’s next
Large efforts test whether your principles travel. I contributed device characterization and SPICE/NN simulations to a **wafer-scale passive crossbar** study (*Nature Communications* 2025). Projects at that scale force rigor: align measurement protocols across labs, check sanity at every stage, and resist the temptation to cherry-pick. In parallel, we examined **neoHebbian** synapses with two state variables—conductance plus a thermal/eligibility term—and evaluated them on RSNN/RL tasks under non-idealities. The through-line stayed the same: model honestly, design accordingly, and validate somewhere you can put a probe or a counter.

Three simple rules keep me oriented:

1. **Start from reality.** Model devices as they are—warts and all.  
2. **Adapt the algorithm.** Co-design learning with the substrate instead of forcing abstraction on the physics.  
3. **Prove it in hardware.** Loihi, FPGA, or RTL/layout—anything you can poke and measure.

Next, I’m extending characterization beyond RRAM (including **eFlash**) and packaging **device-aware spiking IP** for modern SoCs. The goal is boring in the best way: blocks you can drop into a design without a treatise, plus tooling that lets others reproduce results on day one. If you live at the **device → algorithm → hardware** intersection, I’d love to compare notes.

— **Sai**

Advisors: **Prof. Dmitri Strukov** (UCSB) · **Prof. Manan Suri** (IIT Delhi)  
Scholar: <https://scholar.google.com/citations?user=FTYIH9wAAAAJ> · GitHub: <https://github.com/saibez> · LinkedIn: <https://www.linkedin.com/in/saisukruth-bezugam>
