---
title: "6-DOF Robot Manipulator"
description: "Kinematics, workspace analysis, trajectory planning, and simulation studies for a custom six-axis serial manipulator."
date: 2023-07-21
tech: ["MATLAB", "Symbolic Math Toolbox", "Simulink", "MSC ADAMS", "SolidWorks"]
image: "assets/projects/6dof-robot-manipulator/robot-cad.jpg"
tags: ["robotics", "kinematics", "dynamics", "trajectory-planning"]
---

This project studies a custom six-revolute-joint serial manipulator whose joint geometry does not use the conventional three-intersecting-axis wrist. I wrote a custom MATLAB robotics module to explore its kinematics, motion planning, and dynamics using CAD-derived robot parameters.

## Kinematics and workspace

Forward kinematics were derived with the modified Denavit–Hartenberg convention and cross-checked against a screw-theory formulation. The project also implements analytical inverse kinematics using Paden–Kahan subproblems, yielding up to eight candidate configurations for reachable poses. Jacobian analysis was used to study singular configurations and map them into the robot's workspace.

<figure>
  <img src="{{ '/assets/projects/6dof-robot-manipulator/workspace.jpg' | relative_url }}" alt="Three-dimensional reachable workspace of the six-axis manipulator" loading="lazy">
  <figcaption>Computed workspace of the manipulator.</figcaption>
</figure>

## Trajectory and dynamics

A straight Cartesian pick-and-place path was mapped into joint space and parameterized with a smooth, three-second quintic trajectory. A custom MATLAB module with the Symbolic Math Toolbox generated the manipulator's mass, velocity, and gravity terms, which were used to calculate a joint-torque profile.

<figure>
  <img src="{{ '/assets/projects/6dof-robot-manipulator/trajectory.jpg' | relative_url }}" alt="Planned Cartesian path with end-effector orientation frames" loading="lazy">
  <figcaption>Planned Cartesian path and orientation frames for the pick-and-place motion.</figcaption>
</figure>

## Simulation study

The analytical dynamics were compared with a multibody model through MSC ADAMS and Simulink. A separate simulation perturbed mass, inertia, and center-of-mass parameters by up to 10% to study the control response. These are simulation studies; the project materials do not report tests on physical hardware.

## Simulation model

The report includes a Simulink block diagram for the control and dynamics simulation.

<figure>
  <img src="{{ '/assets/projects/6dof-robot-manipulator/simulink-model.jpg' | relative_url }}" alt="Simulink block diagram for the manipulator simulation" loading="lazy">
  <figcaption>Simulink block diagram from the project report.</figcaption>
</figure>
