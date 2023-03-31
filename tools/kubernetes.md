---
description: Orchestration tool
---

# ⚙ Kubernetes

Also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.

## Components

<figure><img src="../.gitbook/assets/изображение (1).png" alt=""><figcaption></figcaption></figure>

* Node or "Worker Node" - virtual or physical machine
* Master Node - Main Node for cluster
* Pod - abstraction over container. Usually 1 Pod = 1 App
* Service - static address for Pod (not connected with Pod lifecycle)
* Ingress - routs traffic to k8s cluster and sends to services inside k8s
* ConfigMap - keeps external config of application. could keep env. vars
* Secret - same as config map, encoded in base64 + should be secure encoded
* Volume - storage for data local (inside Node) or remote
* Deployment - 'blueprint' for Pods configuration
* StatefulSet 'sts' - component for stateful apps or DB
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

### Pod

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### Service

Could be internal or external.&#x20;

Has permanent ip address and works as load balancer if there is more than one Pod

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

### Config Map and Secrets

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

### Volume

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Stores data. Could be local or remote

### Virtual Network

Virtual Network provides connection between nodes. "Creates one unified machine". Each Pod get internal IP address. If Pod will be restarted - IP will be chanegd.





