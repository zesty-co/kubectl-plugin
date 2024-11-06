- [Zesty kubectl plugin](#zesty-kubectl-plugin)
  - [Installation](#installation)
    - [Using krew (recommended)](#using-krew-recommended)
      - [Uninstallation](#uninstallation)
    - [Manual (not recommended)](#manual-not-recommended)
  - [Usage](#usage)
  - [Changelog](#changelog)
    - [v2.2](#v22)
    - [v2.1.1](#v211)
    - [v2.1.0](#v210)
    - [v2.0.0](#v200)
    - [v1.0.1](#v101)

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

> [!NOTE]
> If you are on MacOs or Linux and receiving the following error
> ```bash
> error: unknown command "zesty" for "kubectl"
> ```
> run the following command to make sure the plugin is executable:
> ```bash
> chmod +x ~/.krew/store/zesty/*/kubectl-zesty
> ```

## Changelog

### v2.2

Added a command to collect persistent volumes' usage and utilization

### v2.1.1

Logs collection command:
- Improved volumeattachments' collection

### v2.1.0

Logs collection command:
- Added collection for Zesty's internal Mutator and Extender pods

### v2.0.0

Compatible with zesty-helm version 1.0.253 (new naming convention for internal Zesty resources)

### v1.0.1

Logs collection command:
- Bug fix: Displaying an error message and continuing to collect subsequent resource YML or log instead of exiting upon encountering an error.
