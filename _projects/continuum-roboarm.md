---
title: "Continuum RoboArm"
description: "Data-driven dynamic modeling of a two-segment, tendon-driven continuum robotic arm using ARX/ARMAX, GA-tuned polynomial, and NARX neural network models."
date: 2024-06-18
tech: ["MATLAB", "System Identification", "Genetic Algorithm", "Neural Networks", "Robotics"]
link: "https://github.com/Armangb1/Continuum-RoboArm"
image: "assets/projects/continuum-roboarm/roboarm-hero.jpg"
tags: ["robotics", "system-identification", "machine-learning", "thesis"]
---

Continuum robots — arms with no rigid joints, capable of bending continuously along their length — are attractive for minimally invasive surgery and confined-space work, but their (theoretically infinite) degrees of freedom make first-principles dynamic modeling either too slow for real-time control or too inaccurate to be useful.

This project, my B.Sc. thesis at K. N. Toosi University of Technology, takes a **data-driven system identification** approach instead. I built and instrumented a two-segment, tendon-driven continuum arm ("RoboArm") — 6 Dynamixel motors, 6 load cells for tendon force, dual-camera end-effector tracking — then:

1. Calibrated the force-sensing load cells and closed a discrete PID force-feedback loop around each tendon.
2. Designed a safe, information-rich excitation signal (equilibrium force grid + band-limited noise, saturation-limited) to sweep the full workspace.
3. Collected input/output data and split it sequentially into train/validation/test sets.
4. Identified and compared linear (ARX/ARMAX), quadratic-in-parameters (GA-selected regressors), and NARX neural network models — both as open-loop **simulators** and one-step-ahead **predictors**.

**Outcome:** the NARX neural network gave the best simulation accuracy (up to 81% fit), while ARMAX matched it almost exactly for one-step-ahead prediction (up to 91% fit) at a fraction of the computational cost — making it a strong candidate for real-time model-predictive control of the arm.

<img src="{{ '/assets/projects/continuum-roboarm/demo.gif' | relative_url }}" alt="Real-time trajectory tracking next to the physical robot">


