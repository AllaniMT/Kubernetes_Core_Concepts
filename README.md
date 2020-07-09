# Kubernetes Core Concepts
## Defintion of kubernetes Objects(Various examples)

- Make Sure to install kubernetes and minikube and run ``` minikube start ``` (To create a kubernetes cluster that contain one node).
- To show  graphically the status of all pods, you can run ``` minikube dashboard ``` .
- To show all pods, that exist in the node, run ``` kubectl get pods ``` .

#### Def-Pod

-Or we can create this pod with the imperative way. To make this, run ``` kubectl run my-first-pod-name --image=nginx --restart=Never ```
