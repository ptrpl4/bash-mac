---
description: Orchestration tool
---

# ⚙ Kubernetes

Also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.

#### Therms

Node or "Worker Node" - virtual or physical machine

Master Node - Main Node

## Components

<figure><img src="../.gitbook/assets/изображение (1).png" alt=""><figcaption></figcaption></figure>

* Pod - abstraction over container. Usually 1 Pod = 1 App
* Service
* Ingress
* ConfigMap
* Secret
* Deployment
* StatefulSet
* DaemonSet

## Architecture

K8s cluster contains of:

* At least one **Master Node** (virtual or physical machine)
* Multiple **Worker Nodes** with **kubelet** process ("node agent") on it.

**kubelet** - allows running application processes and communicate&#x20;

**Apps** are running on Worker Nodes.

### Master Node

On Master Node are running **Main k8s Processes** to run and manage cluster. Better to use multiple.

#### Master Node Processes

<figure><img src="../.gitbook/assets/изображение (3).png" alt=""><figcaption></figcaption></figure>

* API Server entrypoint to cluster
  * Access through **UI/API/CLI**
* Controller Manager
  * Monitoring what's going on in cluster
* Scheduler
  * controls the placement of the pods depending on the load
* etcd
  * key-value storage\
    storing info and configs. etcd snapshots are using for backup
  * makes snapshots for recovering proccees&#x20;

### Virtual Network

Virtual Network provides connection between nodes. "Creates one unified machine". Each Pod get internal IP address. If Pod will be restarted - IP will be chanegd.





