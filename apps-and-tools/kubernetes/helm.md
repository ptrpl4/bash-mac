---
description: package manager for Kubernetes
---

# ⛑️ Helm

#### links

* [https://helm.sh/](https://helm.sh/)

### components

* `Chart.yaml` Contains metadata about the chart, such as its name, version, and dependencies.
* `values.yaml` Sets default values for the chart, which can be overridden during installation or upgrade.
* **templates/**: Contains template files that generate Kubernetes manifest files. These templates use the values from `values.yaml` to customize the deployment.
* **charts/**: Stores any chart dependencies defined in `Chart.yaml`.
