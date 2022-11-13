---
description: Orchestration tool
---

# ⚙ Kubernetes

### Architecture

* At least one **Master Node** (virtual or physical machine)
* Multiple **Worker Nodes** with kubelet process ("node agent") on it.

**Apps** are running on Worker Nodes.

On Master Node are running **Main k8s Processes** to run and manage cluster.

k8s processes on Master Node:

* API Server entrypoint to cluster
  * Access through UI/API/CLI
* Controller Manager
  * Monitoring what's going on
* Scheduler
  * ensures Pods placements
* etcd
  * storing info and configs. etcd snapshots are using for backup

Virtual Network provides connection between nodes. "Creates one unified machine". Each Pod get internal IP address. If Pod will be restarted - IP will be chanegd.

### Components

Node - virtual or physical machine

Pod - abstraction over container. Usually 1 Pod = 1 App

Service

Ingress

ConfigMap

Secret

Deployment

StatefulSet

DaemonSet

