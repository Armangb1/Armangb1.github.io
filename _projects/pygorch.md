---
title: "Gorch"
description: "From-scratch automatic differentiation and neural network library in pure NumPy with hand-written backward passes, 14 optimizers, and control tools (Kalman filter, RLS, EKF)."
date: 2024-12-01
tech: ["Python", "NumPy", "Automatic Differentiation", "Neural Networks", "Control Systems", "Optimization", "Machine Learning"]
link: "https://github.com/Armangb1/pygorch"
image: "assets/projects/pygorch/hero3.svg"
---

Gorch is a from-scratch automatic differentiation and neural-network library written purely in NumPy — no PyTorch, no TensorFlow. Built for a Neural Control course at K. N. Toosi University of Technology, it demonstrates exactly how backpropagation, optimizers, and network layers work under the hood.

The library features hand-written autograd where every differentiable operation wraps its inputs in a dedicated `*Backward` node implementing the local gradient rule, making the full reverse-mode chain explicit and readable. The `gorch.Tensor` API provides `requires_grad`, `.backward()`, `.grad`, and PyTorch-style operators (`+`, `@`, `*`, `sin`, `exp`, `relu`, `softmax`, `mean`, `max`, `norm`, ...).

Neural network components include `nn.Linear`, `nn.Sequential`, activations, and losses (`MSELoss`, `CrossEntropyLoss`, `BCELoss`, `L1Loss`) with `state_dict`/`save`/`load` serialization. Fourteen optimizers are implemented: SGD, SGD-Momentum, Adam, Adamax, NAdam, AMSGrad, RMSprop, Adagrad, Adadelta, Nesterov, PID, Levenberg–Marquardt, and more.

Control-flavored tools include `KalmanFilter`, `EKFOptimizer` (extended-Kalman neural identification), and `RLS` for online system identification, plus a hand-rolled `jacobian`. All gradients are verified against finite differences in the test suite.

The codebase is organized into `gorch.tensor` (Tensor, reverse-mode graph, differentiable ops), `gorch.nn` (Module, layers, activations, losses, functional helpers), `gorch.optim` (gradient-descent and adaptive optimizers plus Kalman filter and online-identification optimizers), and `gorch.utils` (datasets and data-loading helpers).
