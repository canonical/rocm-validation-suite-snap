# ROCm Validation Suite Snap

[![rocm-validation-suite][snap-badge]][snap-link]
[![CI][ci-badge]][ci-link]

This is a snap packaging of [ROCm Validation Suite][rocm/rocmvalidationsuite],
a system validation and diagnostics tool for monitoring, stress testing,
detecting, and troubleshooting issues impacting AMD GPUs in high-performance
computing environments.

## Install

```shell
sudo snap install rocm-validation-suite
```

This snap consumes ROCm runtime libraries provided by `rocm-inference`, which should be installed automatically, but might need a manual interface connection:

```shell
sudo snap install rocm-inference
sudo snap connect rocm-validation-suite:rocm rocm-inference:runtime
```

[![Get it from the Snap Store](https://snapcraft.io/en/dark/install.svg)][snap-link]

([Don't have snapd installed?][snapd-setup])

## Use

For usage instructions refer to the [ROCm Validation Suite documentation].

[ci-badge]: https://github.com/canonical/rocm-validation-suite-snap/actions/workflows/ci.yaml/badge.svg
[ci-link]: https://github.com/canonical/rocm-validation-suite-snap/actions/workflows/ci.yaml
[rocm validation suite documentation]: https://rocm.docs.amd.com/projects/ROCmValidationSuite/en/latest/
[rocm/rocmvalidationsuite]: https://github.com/ROCm/ROCmValidationSuite
[snap-badge]: https://snapcraft.io/rocm-validation-suite/badge.svg
[snap-link]: https://snapcraft.io/rocm-validation-suite
[snapd-setup]: https://snapcraft.io/docs/core/install
