# Kubernetes Core Concepts
## Defintion of kubernetes Objects(Various examples)

- Make Sure to install kubernetes and minikube and run ``` minikube start ``` (To create a kubernetes cluster that contain one node).
- To show  graphically the status of all pods, you can run ``` minikube dashboard ``` .
- To show all pods, that exist in the node, run ``` kubectl get pods ``` .

#### 1 - Def-Pod

- To create pod from the yaml file, run ``` kubectl create -f def-pod.yml ``` . (Declarative way)
- Or we can create this pod with the imperative way. To make this, run ``` kubectl run my-first-pod-name --image=nginx --restart=Never ``` .
- To show more info about the pod, run ``` kubectl logs my-first-pod-name``` .
- To delete the pod, run ````kubectl delete pods my-first-pod-name ``` .
- To specify a port (and listen to it) for a certain pod, run ``` kubectl port-forward pods/my-first-pod-name 8000 ``` .
- To execute and the show the application, that i run in the pod, run ``` kubectl exec -it my-first-pod-name bash ```` .

#### 2 - Def-ReplicaSet

- To create a Replica from the yaml file, run ``` kubectl create -f def-pod.yml ``` .
- The aim of Replicaset is to determine how many times the same pod repeats. If one fails, kubernetes creates another to ensure, that the number of pods remains the same.
