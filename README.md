- [Zesty kubectl plugin](#zesty-kubectl-plugin)
  - [Installation](#installation)
    - [Using krew (recommended)](#using-krew-recommended)
      - [Uninstallation](#uninstallation)
    - [Manual (not recommended)](#manual-not-recommended)
  - [Usage](#usage)
  - [Changelog](#changelog)
    - [v3.0.1](#v301)
    - [v3.0.0](#v300)
    - [v2.3.1](#v231)
    - [v2.3.0](#v230)
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

4. Verify a successful installation:

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

Download the latest version from the [releases](https://github.com/zesty-co/kubectl-plugin/releases) page and unzip the executable to a directory which is accessible on PATH.

## Usage

Run `kubectl zesty --help` for available functionality.

> [!NOTE]
> If you are on MacOs or Linux and receiving the following error
> ```bash
> error: unknown command "zesty" for "kubectl"
> ```
> run the following command to make sure the plugin is executable:
> ```bash
> chmod +x ~/.krew/store/zesty/*/kubectl-zesty
> ```

### pod-placement status

Shows Pod Placement savings data, workload evictability breakdown, and cluster summary by connecting to the Kompass Insights Agent running in your cluster.

**Examples:**

```bash
# Show full pod placement status in table format
kubectl zesty pod-placement status

# Show only the cluster summary
kubectl zesty pod-placement status --summary

# Output as JSON
kubectl zesty pod-placement status -o json

# Use a specific namespace and kubeconfig context
kubectl zesty pod-placement status --namespace zesty-system --context my-cluster

# Pipe to a file without headers
kubectl zesty pod-placement status --no-headers > status.csv
```

**Flags:**

| Flag | Short | Default | Description |
|------|-------|---------|-------------|
| `--namespace` | | `""` | Namespace of the Insights Agent service (auto-detected if empty) |
| `--service-name` | | `""` | Name of the Insights Agent service (auto-detected if empty) |
| `--output` | `-o` | `table` | Output format: `table`, `json`, `yaml` |
| `--summary` | | `false` | Show only the cluster summary |
| `--context` | | `""` | Kubernetes context to use (defaults to current context) |
| `--timeout` | | `30s` | HTTP request timeout |
| `--verbose` | `-v` | `false` | Enable verbose logging for debugging |
| `--log-level` | | `info` | Log level: `debug`, `info`, `warn`, `error` |
| `--insecure-skip-tls-verify` | | `false` | Skip TLS certificate verification (not recommended for production) |
| `--no-headers` | | `false` | Omit table headers (useful for CSV-style piping) |

## Changelog

### v3.0.1

Improved pod-placement status command behavior and error handling.

### v3.0.0

Added pod-placement status functionality

### v2.3.1

Fix: EZSwitch auto-migrate

### v2.3.0

Added ezswitch commands

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
