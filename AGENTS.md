# Preface

This repository packages the upstream [ROCm Validation Suite](https://github.com/ROCm/ROCmValidationSuite) (RVS) as a strict-mode snap. The content in this file and directory is relevant only to tasks about building, packaging, releasing, or maintaining this snap, and to this repository's CI, documentation, and knowledge base. It is not relevant to changes in the upstream RVS source code.

Read the top-level `.kb/agents.md` file before continuing below.

# Overview

Snap packaging of the upstream ROCm Validation Suite (RVS), a system validation and diagnostics tool for monitoring, stress testing, detecting, and troubleshooting issues affecting AMD GPUs in high-performance/AI/ML computing environments. It ships a single strict-mode snap (`rocm-validation-suite`) built from the upstream git tag via snapcraft.

# Architecture

The snap is built from a single cmake part that fetches the upstream RVS source at the `rocm-${SNAPCRAFT_PROJECT_VERSION}` git tag and installs it under `/opt/rocm-<version>` inside the snap. AMD's `repo.radeon.com` apt repositories (amdgpu and rocm, suite `noble`) supply the ROCm build and runtime dependencies. A single strict-mode app entry point, `rocm-validation-suite`, invokes `rvs` with its library and binary paths wired into `$SNAP`, and plugs several super-privileged interfaces (hardware-observe, power-control, process-control, system-observe, and others) required to probe the GPU.

# Directory

- `.kb/` - Agent knowledge base (see Documents).
- `.pre-commit-config.yaml` - Pre-commit hooks.
- `AGENTS.md` - This file; top-level agent guidance.
- `CONTRIBUTING.md` - Prerequisites and contribution instructions.
- `README.md` - Project introduction and install/usage pointers.
- `snap/` - Snapcraft source directory; contains the full snap definition.

# Documents

- `.kb/agents.md` - General rules for the knowledge base reading and writing.
