- [Zesty kubectl plugin](#zesty-kubectl-plugin)
  - [Installation](#installation)
    - [Using krew (recommended)](#using-krew-recommended)
      - [Uninstallation](#uninstallation)
    - [Manual (not recommended)](#manual-not-recommended)
  - [Usage](#usage)

# Zesty kubectl plugin

Used to interact with Zesty's resources

## Installation

### Using [krew](https://krew.sigs.k8s.io/) (recommended)

1. Add this repo as a krew index
   
   ```bash
   $ kubectl krew index add zestyIndex https://github.com/zesty-co/kubectl-plugin.git
   ```

2. Verify it was added successfully

   ```bash
   $ kubectl krew index list
   INDEX       URL
   default     https://github.com/kubernetes-sigs/krew-index.git
   zestyIndex  https://github.com/zesty-co/kubectl-plugin.git
   ```

3. Install the plugin:
   
   ```bash
   $ kubectl krew install zestyIndex/zesty
   ```

4. Verify a successul installation:

   ```bash
   $ kubectl krew list
   PLUGIN          VERSION
   zestyIndex/zesty  v1.0.0
   ```

#### Uninstallation

```bash
kubectl krew uninstall zesty
```

### Manual (not recommended)

Download the latest version from the [releases](https://github.com/zesty-co/kubectl-plugin/releases) page and unzip the executable to a directory which is accessable on PATH.

## Usage

Run `kubectl zesty --help` for availble functionality.
