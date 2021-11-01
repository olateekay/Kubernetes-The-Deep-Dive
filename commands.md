*To find the image used to create a pod, run this*
` kubectl describe pod <name of pod> | grep -i image `


*this command shows you the nodes in which pods are placed*

`kubectl get pods -o wide `


*Create an NGINX Pod*

`kubectl run nginx --image=nginx`

*Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run)*

`kubectl run nginx --image=nginx --dry-run=client -o yaml`

*Create a deployment*

`kubectl create deployment --image=nginx nginx`

*Generate Deployment YAML file (-o yaml). Don't create it(--dry-run)*

`kubectl create deployment --image=nginx nginx --dry-run=client -o yaml`

*Generate Deployment YAML file (-o yaml). Don't create it(--dry-run) with 4 Replicas (--replicas=4)*

`kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > nginx-deployment.yaml`

*Save it to a file, make necessary changes to the file (for example, adding more replicas) and then create the deployment.*

`kubectl create -f nginx-deployment.yaml`

OR

*In k8s version 1.19+, we can specify the --replicas option to create a deployment with 4 replicas.*

`kubectl create deployment --image=nginx nginx --replicas=4 --dry-run=client -o yaml > nginx-deployment.yaml`

*Deploy a pod called "my-pod" using the nginx:alpine image*

`kubectl run my-pod --image=nginx:alpine`

If you are a Kubernetes beginner you should know that this is not a common way to run Pods. The common way is to run a Deployment which in turn runs Pod(s).
In addition, Pods and/or Deployments are usually defined in files rather than executed directly using only the CLI arguments.

*What are your thoughts on "Pods are not meant to be created directly"?*

Pods are usually indeed not created directly. You'll notice that Pods are usually created as part of another entities such as Deployments or ReplicaSets.
If a Pod dies, Kubernetes will not bring it back. This is why it's more useful for example to define ReplicaSets that will make sure that a given number of Pods will always run, even after a certain Pod dies.

*How many containers can a pod contain?*

A pod can include multiple containers but in most cases it would probably be one container per pod.

Another way to check what's going on, is to run 
`kubectl logs <POD_NAME>`
 This will provide us with the logs from the containers running in that Pod.


Run the command: 

`kubectl describe node node01 | grep -i taints`

 to check taint exists.


 Create a taint on node01 with key of spray, value of mortein and effect of NoSchedule

 Run the command: kubectl taint nodes node01 spray=mortein:NoSchedule


 number of daemon set in cluster in all namespace 
 `kubectl get ds --all-namespaces`

 `kubectl top node`
 `kubectl top pod`