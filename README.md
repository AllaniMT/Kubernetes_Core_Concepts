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
- To execute and  show the application, that i run in the pod, run ``` kubectl exec -it my-first-pod-name bash ```` .

#### 2 - Def-ReplicaSet

- To create a Replica from the yaml file, run ``` kubectl create -f def-replicaset.yml ``` .
- The aim of Replicaset is to determine how many times the same pod repeats. If one fails, kubernetes creates another to ensure, that the number of pods remains the same. (In my case, i created the nginx container in 4 different pods)
- To show, how much pods we have, run ``` kubectl get pods ``` .
- To show the status of our ReplicaSet, run ``` kubectl get replicasets ``` .
- We delete a pod with the command  ``` kubectl delete pods my-first-pod-name ```, to see how kubernetes create another pod, to ensure the number of pods remains the same.

###### Scalling up/down the number of pods

- Imperative way: ````kubectl scale --replicas=6 replicaset my-replicaset-name ``` . (Here i make the   number of pods in the replicasets from 4 to 6)
- Declarative way: 
    * Chnage the number of pods in the yaml file
    * And run, ``` kubectl replace -f def-replicaset.yml ``` .
  
