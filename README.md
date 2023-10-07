## install with k3s
### useful websites 
1. [diffrent ways to install kubernetes](https://kubedemy.io/ssbostan/kubernetes-installation-methods-the-complete-guide-update-2022)
1. [useful posts about k8](https://kubedemy.io/)
1. [saeed boostani website](https://devops-with-saeid.com/)
1. [easy way to make a k8 cluster](https://k3s.io/)
1. [an other way to setup k8 ](https://kubespray.io/#/)
1. [an other way to setup k8 ](https://kubespray.io/#/](https://k3s.io/)

```bash
curl -sfL https://get.k3s.io | sh - 
# Check for Ready node, takes ~30 seconds 
sudo k3s kubectl get node 
```

### test that your master node works or not ? 

```bash
kubectl get node
```

### prompt complition for a any type of shell

```bash
kubectl completion bash > /etc/bash_completion.d/kubectl && bash
```
### access to k8 cluster is achive with `cube config` file

## in k3s your cube config file is stored in 
`cat /etc/rancher/k3s/k3s.yaml`

> `cubectl` needs to have access to your cube config file there is 2 ways that you can give access to it 

1. file needs to be in `~/.cube/config` directory
1. export KUBECONFIG=/path/to/your/config



### every object in k8s are accessable with something called manifest

> you can see all of your available resources with 

```bash 
kubectl api-resources
```

there are 3 main thing you have to know about the resource you are about to use when you are writing your manifest

1. api version that is require for that resource you want to use 
1. KIND of that resource
1. and details about that resource which you can find with following command

```bash 
kubectl explain <your resource KIND name>
```
for example :

```bash 
kubectl explain pods
```
> you can have extera details about specific detail of resource with 

```bash 
kubectl explain <your resource KIND name>.status
```
for example :

```bash 
kubectl explain pods.spec
```


### your cluster namespaces can be shown with 

```bash
kubectl get ns
```

> we said that using all type of resources need a manifest 

> let say you wanna create a pod of nginx for that you create a file called `pod.yml` 

> all types of kubernetes api are done with a json or yml style file 

> after you create your anifest you have to apply it with following command :

```bash
kubectl apply -f pod.yml
```
> you can list all of your avaiable pods with : 

```bash 
kubectl get pod

```

### you can get extera information of your existing pods with 

```bash
kubectl get pod -o wide
```

### you can get extera information of your existing nodes with 

```bash
kubectl get node -o wide
```

### for deletion of a existing pod 

```bash 
kubectl delete pod test
```

### for high avaiablilty you can  use `replica-sets` :

```bash 
kubectl api-resources
```

```bash 
kubectl explain replica-sets
```

### now that you know about fetures and details of replica-sets you have to write a manifest for that :

### replica-sets goals :
1. desired state
1. self yelling
1. scaling
not upgrade 

###deployment goals :
1. rollout (uppgrade)
1. rollback (downgrade)


deployment <-- replica-sets

if you run `kubectl get rs` you can see that deployment already created a rs by it self and after you change your desired state



deployment sits on top of replica-sets and its perpose is only updating apps of a desired monifest

best practice tag images strategy :
1. tag latest
1. tag git commit
1. tag major version
1. tag major minor 
1. tag major minor patch


private registery :
1. ECR AWS
1. zot selfhosted registery
1. harbor self hosted registry


practice : 

apply a deployment and try to roll back roll out and scale your pods 


t.me/shirazcloud
