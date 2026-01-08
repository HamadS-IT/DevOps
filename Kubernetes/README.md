# Kubernetes and Its Architecture

## Overview
Kubernetes (also known as **K8s**) is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerized applications. It abstracts the underlying infrastructure and provides a consistent way to run applications across different environments.

Originally developed by Google, Kubernetes is now maintained by the **Cloud Native Computing Foundation (CNCF)**.

---

## Why Kubernetes?
Kubernetes helps solve common challenges in containerized environments, such as:
- Application scaling
- High availability
- Load balancing
- Automated rollouts and rollbacks
- Resource management
- Service discovery

---

## Kubernetes Architecture
Kubernetes follows a **master–worker (control plane–node)** architecture.

### High-Level Architecture
```

+-------------------+
|   Control Plane   |
+-------------------+
|
-

|           |              |
Node 1     Node 2         Node N

```

---

## Control Plane Components
The **Control Plane** manages the overall state of the cluster.

### 1. kube-apiserver
- Acts as the front-end of the Kubernetes cluster
- Exposes the Kubernetes API
- Handles all REST requests (kubectl, controllers, nodes)

### 2. etcd
- Distributed key-value store
- Stores cluster state and configuration data
- Highly available and consistent

### 3. kube-scheduler
- Assigns Pods to nodes
- Makes scheduling decisions based on:
  - Resource availability
  - Constraints
  - Affinity rules

### 4. kube-controller-manager
- Runs background controllers
- Ensures the desired state matches the actual state
- Examples:
  - Node Controller
  - Replication Controller
  - Endpoint Controller

### 5. cloud-controller-manager (optional)
- Integrates Kubernetes with cloud providers
- Manages cloud-specific resources like:
  - Load balancers
  - Volumes
  - Nodes

---

## Node Components
Each **Node** runs application workloads.

### 1. kubelet
- Agent running on each node
- Communicates with the API server
- Ensures containers are running as expected

### 2. Container Runtime
- Runs containers
- Examples:
  - containerd
  - CRI-O
  - Docker (deprecated in newer versions)

### 3. kube-proxy
- Handles networking rules
- Enables service discovery and load balancing
- Manages iptables or IPVS rules

---

## Core Kubernetes Objects

### Pod
- Smallest deployable unit
- Contains one or more containers
- Shares network and storage

### Service
- Exposes Pods internally or externally
- Provides stable networking and load balancing

### Deployment
- Manages stateless applications
- Supports rolling updates and rollbacks

### ReplicaSet
- Ensures a specified number of Pod replicas are running

### ConfigMap & Secret
- Store configuration and sensitive data separately from code

---

## Kubernetes Networking
- Each Pod gets a unique IP address
- Pods can communicate across nodes without NAT
- Services provide stable endpoints
- Ingress manages external HTTP/HTTPS traffic

---

## Kubernetes Storage
- Uses **Volumes** to persist data
- Supports:
  - Persistent Volumes (PV)
  - Persistent Volume Claims (PVC)
- Works with cloud and on-prem storage systems

---

## Kubernetes Workflow
1. User submits a request (e.g., `kubectl apply`)
2. API Server validates the request
3. Desired state is stored in etcd
4. Scheduler assigns Pods to nodes
5. kubelet creates containers
6. Controllers continuously monitor and reconcile state

---

## Advantages of Kubernetes
- Scalability
- High availability
- Portability
- Self-healing
- Declarative configuration

---

## Conclusion
Kubernetes provides a powerful and flexible platform for running modern, containerized applications. Its modular architecture and strong ecosystem make it the industry standard for container orchestration.

---

## References
- https://kubernetes.io/docs/
- https://github.com/kubernetes/kubernetes


# Explaining:

- How to Install `Kubernetes` and Create a `Multi-Node Cluster` Using `Kind`?
