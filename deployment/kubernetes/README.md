# Kubernetes notes

### minikube
```bash
minikube version
minikube start # start a cluster
```

### kubectl commands
```bash
kubectl version
kubectl cluster-info # view cluster details
kubectl get nodes # show all nodes that can be used to host our applications
kubectl run deployment_name --image=dockerhub/user/image:tag --port=if_you_want_other_port # the run command creates a new deployment
kubectl get deployments # list your deployments
kubectl proxy # creates a route between our host and the kubernetes cluster using proxy
kubectl get # list resources
kubectl describe # show detailed information about a resource
kubectl logs # print the logs from a container in a pod
kubectl exec # execute a command on a container in a pod
```
