# CKA-Preparation
Préparation de la certification CKA 

# Exam

Cluster Architecture, Installation & Configuration (25%)

Helpful commands:

```bash
# Display addresses of the master and services
kubectl cluster-info

# Dump current cluster state to stdout
kubectl cluster-info dump

# List the nodes
kubectl get nodes

# Show metrics for a given node
kubectl top node my-node

# List all pods in all namespaces, with more details
kubectl get pods -o wide --all-namespaces

# List all services in all namespaces, with more details
kubectl get svc  -o wide --all-namespaces
```
## Cluster Architecture, Installation & Configuration (25%)
## Workloads & Scheduling (15%)
## Services & Networking (20%)
## Storage (10%)
## Troubleshooting (30%)
