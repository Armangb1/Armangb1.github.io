---
title: "Data-Driven Control Toolbox"
description: "Companion MATLAB/Simulink toolbox to Khaki-Sedigh's 'An Introduction to Data-Driven Control Systems' — DeePC, MFAC, unfalsified switching (single- and multimodel), SPSA, STR, and VRFT, shipped as a single Simulink block library."
date: 2026-09-07
tech: ["MATLAB", "Simulink", "Data-Driven Control", "Predictive Control", "Adaptive Control", "System Identification"]
link: "https://github.com/Armangb1/data-driven-control-toolbox"
tags: ["control-systems", "simulink", "data-driven-control", "adaptive-control", "educational"]
---

A companion MATLAB/Simulink toolbox implementing every methodology in Ali Khaki-Sedigh's *An Introduction to Data-Driven Control Systems* (Wiley, 2024) — so each technique has directly runnable, tested code mapped to the corresponding book chapter.

**Problem.** Concepts like the Fundamental Lemma, data-enabled predictive control, model-free dynamic linearization, and unfalsified switching are intellectually clear but notoriously fiddly to get right in code: Hankel-matrix construction, persistency-of-excitation conditions, candidate-bank cost functions, and online estimation all hide subtle bugs. Students and researchers needed an implementation they could trust as a reference, usable both interactively and inside Simulink.

**Approach.** The toolbox is built as a MATLAB package namespace (`ddc.*`) with one category per chapter — `ddc.common` (Hankel matrices, persistency-of-excitation checks, sliding-window buffers, RLS, PRBS/multisine excitation), `ddc.deepc` (Data-Enabled Predictive Control), `ddc.mfac` (compact-form dynamic linearization), `ddc.ufc` (single- and multimodel unfalsified switching), `ddc.spsa` (Simultaneous Perturbation Stochastic Approximation), `ddc.str` (direct/indirect self-tuning regulator baselines), and `ddc.vrft` (Virtual Reference Feedback Tuning). Every stateful algorithm is a `matlab.System` class, so the same code runs both as a Simulink "MATLAB System" block and as a plain MATLAB object for offline simulation and scripting. A single consolidated library (`ddc_lib.slx`) registers one browsable "Data-Driven Control Toolbox" node in the Simulink Library Browser with category subsystem folders (Common Utilities, DeePC, MFAC, Unfalsified Switching, SPSA, STR Baselines). Everything ships with a self-contained `matlab.unittest` suite that needs no third-party toolboxes.

**Outcome.** The toolbox provides a complete, tested, chapter-mapped reference implementation of data-driven control — packaged as a distributable `.mltbx` via the Toolbox Packager API, documented with a contributing guide, code of conduct, and citation metadata, and installable either from the Add-On Explorer or directly from the repository.