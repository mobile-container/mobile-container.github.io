![license](https://img.shields.io/badge/Platform-Android-green "Android")
![license](https://img.shields.io/badge/Licence-Apache%202.0-blue.svg "Apache")

## Table of Contents
- [Introduction](#introduction)
- [Code and Data Release](#code-and-data-release)

## Introduction

Cloud execution of mobile apps---running unmodified apps inside full mobile OSes on commodity servers---is gaining adoption
for uses such as GUI agent training and large-scale app testing.
These workloads are both temporally dynamic (from second-scale agent interactions to hour-long tests) and
highly bursty (up to hundreds of concurrent jobs), demanding an elastic platform that can provision mobile environments quickly and at high concurrency.

Existing stacks fall short because each tenant must cold-initialize the mobile framework (a large collection of shared libraries and system services)
before any app can run, inflating boot latency.

We present MCon, the first container system with the *framework consolidation* architecture:
the framework is run as a shared, multi-tenant service instead of a per-tenant component.
The core challenge is to practically enable per-tenant isolation on a large framework with no native multi-tenant support.
MCon achieves this from *outside* the framework: by leveraging the fact that apps interact with the framework solely through IPC,
we virtualize the IPC interface to construct private views of framework and device resources.

Compared to the best existing stacks, MCon achieves sub-second (15× as fast) cold tenant allocation and improves instance density to 2.6×,
decisively improving elasticity for cloud-hosted mobile workloads.
MCon has been used to train mobile agents in a major AI company.

![MCon architecture: framework consolidation](figs/our_arch.pdf)

## Code and Data Release

### Figures and reproduction artifacts
All figures used in the paper are included in [`figs/`](figs/).
The scripts/notebooks we used to generate these figures are available in [`scripts/`](scripts/).

### Source code and data
We have obtained permission to release our implementation. However, we are still following relevant internal procedures of the AI company for open source,
so the Android source (which is large) may take some time to publish.

More relevant details (for example, the top-50 apps used and guidelines to reproduce our results) are on their way.
