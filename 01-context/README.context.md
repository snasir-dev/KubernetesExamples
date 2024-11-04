# Kubernetes Context Guide

A **Kubernetes Context** specifies the Kubernetes cluster, user, and namespace used when interacting with your Kubernetes environment. The current context is the cluster that is currently the default for kubectl. All kubectl commands run against that cluster. Contexts allow you to quickly switch between different environments without reconfiguring each time.

**Key Points:**

- **Cluster, User, and Namespace:** A context includes a Kubernetes cluster address, a user authentication method (e.g., kubeconfig file), and a default namespace for your operations.
- **Current Context:** The current context is the cluster that kubectl commands will target by default.
- **Switching Contexts:** You can use the `kubectl config use-context <context-name>` command to switch between different contexts.

**Example:**

Let's say you have two Kubernetes clusters: `dev-cluster` and `prod-cluster`. You can create contexts for each:

```bash
kubectl config set-context dev
kubectl config set-context prod
```

# Kubernetes Context Commands

| **Command**                                           | **Description**                                                                                    |
| ----------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `kubectl config get-contexts`                         | Lists all contexts available in your kubeconfig file, showing current and available contexts.      |
| `kubectl config current-context`                      | Displays the current active context in your Kubernetes configuration.                              |
| `kubectl config use-context <context-name>`           | Switches the active context to `<context-name>`, setting it as the default context for commands.   |
| `kubectl config set-context <context-name>`           | Modifies or sets parameters for an existing context.                                               |
| `kubectl config rename-context <old-name> <new-name>` | Renames an existing context from `<old-name>` to `<new-name>`.                                     |
| `kubectl config delete-context <context-name>`        | Removes a context from the kubeconfig file, making it inaccessible.                                |
| `kubectl config set-cluster <cluster-name>`           | Adds or modifies a cluster entry in the kubeconfig file.                                           |
| `kubectl config set-credentials <user-name>`          | Adds or modifies a user entry in the kubeconfig file.                                              |
| `kubectl config unset <property>`                     | Deletes a specific property, such as a cluster or user, from the kubeconfig file.                  |
| `kubectl config view`                                 | Displays the entire kubeconfig file in use, showing clusters, users, contexts, and other settings. |

## Example Usage

1. **View all available contexts:**

   ```sh
   kubectl config get-contexts
   ```

2. **Switch to a different context:**

   ```sh
   kubectl config use-context <context-name>
   ```

3. **Check the current context:**

   ```sh
   kubectl config current-context
   ```

4. **Rename a context:**

   ```sh
   kubectl config rename-context <old-name> <new-name>
   ```

5. **Delete a context:**
   ```sh
   kubectl config delete-context <context-name>
   ```

## Configuring Contexts

You can create and customize contexts to define specific clusters, users, and namespaces. This is helpful when working across different environments, such as development, staging, and production.

## Further Reading

Refer to the official Kubernetes documentation on [Contexts and Configuration](https://kubernetes.io/docs/concepts/configuration/organize-cluster-access-kubeconfig/) for additional details on managing and organizing contexts.
