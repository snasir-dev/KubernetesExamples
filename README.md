# KubernetesExamples

This repository serves as a learning tool for understanding the core concepts of Kubernetes through hands-on examples. It is designed to help beginners and intermediate users gain practical experience with Kubernetes components, configurations, and best practices.

> [!IMPORTANT]  
> Each directory includes its own `README.md`, which provides an in-depth explanation of the concepts covered within that directory. These READMEs are designed to break down the examples, explain their purpose, and help users understand the practical implementation of Kubernetes concepts.

## Project Overview

The examples in this repository explore various Kubernetes features, including but not limited to:

- Deployments
- Services
- ConfigMaps
- Secrets
- Persistent Volumes and Persistent Volume Claims
- Ingress Controllers
- Health Probes (Liveness, Readiness, Startup)
- Horizontal Pod Autoscaling (HPA)

Each example includes additional notes and explanations to clarify concepts and provide context, making the learning experience more accessible.

## Acknowledgments

Many of the concepts and examples in this repository are taken directly from [K8sAcademy/Fundamentals-HandsOn](https://github.com/K8sAcademy/Fundamentals-HandsOn). These examples have been updated, modified, reorganized with additional personal notes, examples, and explanations to provide further clarity for myself to better follow the concepts more effectively.

Reference Tutorial: [Docker Containers and Kubernetes Fundamentals – Full Hands-On Course](https://www.youtube.com/watch?v=kTp5xUtcalw)

## Prerequisites

Before diving into the examples, ensure you have the following installed and configured:

1. **Kubernetes Cluster**: Use Minikube, Docker Desktop, or any other Kubernetes setup.
2. **kubectl**: Command-line tool for Kubernetes management.
3. **Helm (optional)**: For managing Kubernetes applications.

## How to Use This Repository

1. Clone this repository:
   ```bash
   git clone https://github.com/snasir95/KubernetesExamples.git
   ```
2. Navigate to the desired example directory:
   ```bash
   cd KubernetesExamples/<example-folder>
   ```
3. Follow the instructions in the respective `README.md` or YAML files to deploy resources to your Kubernetes cluster.

## License

This project is distributed under the [MIT License](LICENSE).
