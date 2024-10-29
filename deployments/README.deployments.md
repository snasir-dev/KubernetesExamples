# Kubernetes Deployment Guide

A **Kubernetes Deployment** automates the process of deploying, scaling, and managing containerized applications. It helps ensure your applications run smoothly by handling rollouts, rollbacks, and updates.

This guide provides a beginner-friendly overview of Kubernetes Deployments and the most commonly used commands to manage them.

## Overview

A Kubernetes Deployment allows you to define:

- The container image to deploy.
- The number of replicas (copies) of the application.
- Strategies for rolling out updates to ensure high availability.

Deployments make managing applications in Kubernetes easier and help ensure your applications are always up-to-date and running as expected.

## Common Commands

| **Command**                                                        | **Description**                                                                          |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| `kubectl create deployment <deployment-name> --image=<image-name>` | Creates a new deployment with the specified image.                                       |
| `kubectl get deployments` or `kubectl get deploy`                  | Lists all deployments in the current namespace, showing their status.                    |
| `kubectl describe deployment <deployment-name>`                    | Provides detailed information about a specific deployment.                               |
| `kubectl scale deployment <deployment-name> --replicas=<number>`   | Scales the deployment to the specified number of replicas.                               |
| `kubectl rollout status deployment <deployment-name>`              | Checks the status of a rollout, useful for tracking updates.                             |
| `kubectl rollout restart deployment <deployment-name>`             | Restarts the deployment, causing the pods to be recreated with the latest configuration. |
| `kubectl rollout undo deployment <deployment-name>`                | Rolls back the deployment to a previous version.                                         |
| `kubectl delete deployment <deployment-name>`                      | Deletes a deployment, removing all replicas managed by it.                               |

## Example Usage

1. **Create a Deployment:**

   ```sh
   kubectl create deployment my-deployment --image=nginx
   ```

2. **Scale the Deployment:**

   ```sh
   kubectl scale deployment my-deployment --replicas=3
   ```

3. **Check Deployment Status:**

   ```sh
   kubectl rollout status deployment my-deployment
   ```

4. **Update the Deployment Image:**

   ```sh
   kubectl set image deployment/my-deployment nginx=nginx:latest
   ```

5. **Roll Back to a Previous Version:**
   ```sh
   kubectl rollout undo deployment my-deployment
   ```

## Managing Rollouts

Kubernetes Deployments handle updates with rollouts, ensuring no downtime when updating an application. If an update causes issues, you can use **rollback** commands to revert to a stable version. Rollouts help maintain application availability, even during updates.

## Further Reading

Refer to the official Kubernetes documentation on [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) for additional details and advanced options.
