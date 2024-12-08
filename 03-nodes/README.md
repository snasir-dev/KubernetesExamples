# Kubernetes Nodes Guide

**Kubernetes Nodes** are the machines (physical or virtual) that run containerized applications in a Kubernetes cluster. Each cluster has **master nodes** to manage and schedule workloads and **worker nodes** to run the actual application containers.

This guide provides an overview of Kubernetes Nodes architecture and commonly used commands for managing nodes.

## Kubernetes Node Architecture

### Master Node Components

The **master node** manages the Kubernetes cluster and controls how workloads are distributed. Its main components include:

- **etcd**: A distributed key-value store used to store all cluster data. It keeps track of the cluster's state and is essential for high availability and fault tolerance.
- **kube-apiserver**: Exposes the Kubernetes API, serving as the entry point for all administrative tasks. It processes requests from `kubectl`, the Kubernetes CLI.
- **kube-scheduler**: Assigns workloads to nodes based on resource availability and policies. It ensures each pod is scheduled to the most suitable node.
- **kube-controller-manager**: Runs controllers that handle routine tasks such as node management, replication, and endpoint configuration.
- **cloud-controller-manager**: Manages interactions with the underlying cloud provider (e.g., for load balancing, node scaling, etc.).

### Worker Node Components

**Worker nodes** host the containers that run the applications. Each worker node has the following components:

- **kubelet**: The main node agent, which ensures that containers are running in the pod. It monitors the state of each pod and reports back to the kube-apiserver.
- **kube-proxy**: Manages networking on the node, maintaining network rules that allow communication between pods and services.
- **Container Runtime**: The software responsible for running containers, such as Docker or containerd.

## Common Commands

| **Command**                                              | **Description**                                                                                 |
| -------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `kubectl get nodes`                                      | Lists all nodes in the cluster, showing their status, roles, and version.                       |
| `kubectl describe nodes <node-name>`                     | Shows detailed information about a specific node, including conditions and resource allocation. |
| `kubectl cordon <node-name>`                             | Marks the node as unschedulable, preventing new pods from being scheduled on it.                |
| `kubectl uncordon <node-name>`                           | Marks the node as schedulable, allowing new pods to be scheduled on it.                         |
| `kubectl drain <node-name>`                              | Safely evicts all pods from a node, preparing it for maintenance.                               |
| `kubectl label nodes <node-name> <key>=<value>`          | Adds or updates a label on a node for easier identification or selection.                       |
| `kubectl taint nodes <node-name> <key>=<value>:<effect>` | Applies a taint to a node, controlling which pods can be scheduled on it.                       |
| `kubectl top nodes`                                      | Displays the CPU and memory usage of each node (requires the metrics server).                   |

## Example Usage

1. **List All Nodes:**

   ```sh
   kubectl get nodes
   ```

2. **Show Detailed Node Info:**

   ```sh
   kubectl describe nodes <node-name>
   ```

3. **Drain a Node (e.g., for maintenance):**

   ```sh
   kubectl drain <node-name> --ignore-daemonsets --delete-emptydir-data
   ```

4. **Mark Node as Unschedulable (cordon):**

   ```sh
   kubectl cordon <node-name>
   ```

5. **Check Resource Usage:**
   ```sh
   kubectl top nodes
   ```

## Managing Node Availability

Kubernetes provides commands such as **cordon** and **drain** to manage node availability. This allows you to take nodes in and out of service without affecting application uptime. You can also use **labels** and **taints** to control where specific workloads should be scheduled based on node characteristics.

## Further Reading

Refer to the official Kubernetes documentation on [Nodes](https://kubernetes.io/docs/concepts/architecture/nodes/) for additional details and advanced configuration options.
