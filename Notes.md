First build the image and push it to docker-hub

## Basic commands Cheatsheet

create a deployment

    kubectl create deployment <deployment-name> --image=<you dockerhub-image>

---

expose the deployment ClusterIP, NodePort, LoadBalancer

    kubectl expose deployment <name> --port=port --type:LoadBalancer
---
if you are using minikube :
(run this command in new terminal)

    minikube service <your-service-name>
---
We can create yaml files for configuring our cluster

    kubectl apply -f filename.yaml
---
Get the env variables of a pod:

    kubectl exec -it <pod_name> -- printenv
---
Commands:
get resources (pods, services, deployments etc..)

    kubectl get <resource> -n <namespace>
---
describe a object of resource

    kubectl describe <resource> <object_name>
eg: kubectl describe pvc db-pvc

---
apply yaml files present in a nested directory:

    kubectl apply -f <dir> -R
---
delete all pods:

    kubectl delete pods --all
---
scale a deployment:

    kubectl scale deployment/<object_name> --replicas=<required_num_of_replicas>
---
trigger rollout deployment

    kubectl rollout restart deployments/result-deployment

Note: The image should point to :latest in the deployment configuration file
---
manually set the image of the deployment app

    kubectl set image deployments/<deployment-name> <app-name>/<new-image-name>
---
get the status of deployment:

    kubectl rollout status deployment/<deployment-name>
---
undo a deployment:

    kubectl rollout undo deployment/result-deployment
---
get rollout history:

    kubectl rollout history deployments/result-deployment
---
get information about a specific rollout history:

    kubectl rollout history deployments/<deployment-name> --revision=1

### Note:
- If a current job is not yet finished running Kubernetes will allow running the next job if it is already time to run the next job.
- If we want the job to run on a specific time of day then we need to provide time in UTC..
