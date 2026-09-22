# Contributing

## Pre-requisites

Your user will need to be a member of the following groups to run `rvs`:

```shell
# Create the groups if they don't exist
sudo groupadd -f render
sudo groupadd -f video
# Add your user to the groups
sudo usermod -aG render,video $USER
```

You may need to log out and log back in for the above changes to take effect.

## Recommendations

The project provides [pre-commit] hooks. Feel free to install them:

```shell
# install pre-commit with uv: uv tool install pre-commit
pre-commit install
```

## Packaging

Install [snapcraft]:

```shell
sudo snap install --classic snapcraft
```

Build and package the snap:

```shell
snapcraft pack
```

The above command will create a file in the format of
`rocm-validation-suite_<version>_amd64.snap`. Install the snap:

```shell
sudo snap install --dangerous rocm-validation-suite*.snap
```

The ROCm Validation Suite uses the runtime supplied by the `rocm-inference` content snap. Connect it after installing both snaps:

```shell
sudo snap install rocm-inference
sudo snap connect rocm-validation-suite:rocm rocm-inference:runtime
```

The snap also plugs privileged interfaces that may not auto-connect for a locally-built snap installed with `--dangerous`.
Check the current state and connect the interfaces you need:

```shell
# See which interfaces are connected
snap connections rocm-validation-suite

# Interfaces required for GPU enumeration and ROCm worker initialization
sudo snap connect rocm-validation-suite:hardware-observe
sudo snap connect rocm-validation-suite:process-control

# Interfaces you may need in specific circumstances
sudo snap connect rocm-validation-suite:removable-media
sudo snap connect rocm-validation-suite:system-observe
```

Snap aliases are also not set up automatically with the `--dangerous` flag.
To run the ROCm Validation Suite with just the `rvs` command, run:

```shell
sudo snap alias rocm-validation-suite rvs
```

[pre-commit]: https://pre-commit.com/
[snapcraft]: https://github.com/canonical/snapcraft
