# Kubernetes Core Concepts
## Defintion of kubernetes Objects(Various examples)

- Make Sure to install kubernetes and minikube and run ``` minikube start ``` (To create a kubernetes cluster that contain one node).
- To show  graphically the status of all pods, you can run ``` minikube dashboard ``` .
- To show all pods, that exist in the node, run ``` kubectl get pods ``` .

#### 1 - Def-Pod

- To create pod from the yaml file, run ``` kubectl create -f def-pod.yml ``` . (Declarative way)
- Or we can create this pod with the imperative way. To make this, run ``` kubectl run my-first-pod-name --image=nginx --restart=Never ``` .
- To show more info about the pod, run ``` kubectl logs my-first-pod-name``` .
- To delete the pod, run ``` kubectl delete pods my-first-pod-name ``` .
- To specify a port (and listen to it) for a certain pod, run ``` kubectl port-forward pods/my-first-pod-name 8000 ``` .
- To execute and  show the application, that i run in the pod, run ``` kubectl exec -it my-first-pod-name bash ``` .

#### 2 - Def-ReplicaSet

- To create a ReplicaSet from the yaml file, run ``` kubectl create -f def-replicaset.yml ``` .
- The aim of Replicaset is to determine how many times the same pod repeats. If one fails, kubernetes creates another to ensure, that the number of pods remains the same. (In my case, i created the nginx container in 4 different pods)
- To show, how much pods we have, run ``` kubectl get pods ``` .
- To show the status of our ReplicaSet, run ``` kubectl get replicasets ``` .
- We delete a pod with the command  ``` kubectl delete pods my-first-pod-name ```, to see how kubernetes create another pod, to ensure the number of pods remains the same.

###### Scalling up/down the number of pods

- Imperative way: ``` kubectl scale --replicas=6 replicaset my-replicaset-name ``` . (Here i make the   number of pods in the replicasets from 4 to 6)
- Declarative way: 
    * Chnage the number of pods in the yaml file
    * And run, ``` kubectl replace -f def-replicaset.yml ``` .
  
  #### 3 - Def-Deployments
  
- Deployment is used, when we have to upgrade (or downgrade) Containers without the system failing.(Rolling update => One at the time)
- Deployment is the same like ReplicaSet, We need only to change the kind(wie write "Deployment" instead of ReplicaSet)
- To create a new Deployment, run  ```` Kubectl create -f def-deployment.yml ``` .
- To show, if the Deployment created, run ``` kubectl get deployments ```
- To show, that a new replicaset was created, run ``` kubectl get rs ```  or ``` kubectl get replicasets ```
- To show, if all the pods are running``` kubectl get po ``` or ``` kubectl get pods ```
- To show more information about the deployment ``` kubectl describe deployments  my-deployment-name ```
- To show that,we have only one revision, run  ``` kubectl rollout history deployment/my-deployment-name ``` 
- To delete the deployment, run ``` kubectl delete deployments my-deployment-name ```
- We create now new deployment but with record, ``` kubectl create -f def-deployment.yml ``` . After we run the command ``` kubectl rollout history deployment/my-deployment-name ``` , we see that the change-cause is no more empty. 
- To make sur, that our deployment running, ``` kubectl port-forward deployments/myapp-deploy 3000 ```, Enter in browser "localhost:3000" .
- Now we can modify our container (In our case is: nginx) . And for sure we have to modify the container version in the yaml file.
- To Apply the modification, run ``` kubectl apply -f def-deployment.yml ```
- with the command ``` kubectl rollout history deployment/my-deployment-name ``` we can see that we have two version of deployment
- If we didn't like the new version, we can undo it, with : ``` kubectl rollout undo deployment/my-deployment-name --to-revsion 1``` . And now we have the old version of our container.
