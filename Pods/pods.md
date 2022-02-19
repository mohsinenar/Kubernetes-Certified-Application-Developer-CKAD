# Creat Pod Using yaml files.
## structure 

**wordpress-pod.yaml**
``` Yaml
apiVersion: v1 # <- for pods this v1
kind: Pod # <- kind 
metadata: # <- first part of the file is to describe our pod 
  name: my-pod # <- a specific name for the pod
  labels: # <- labels to tag the pod
    app: cms-wordpress # <- key: value paires can be a list 
    key: value
spec: # <- second part to specify the desired state of the pods
  containers: # <- list of containers: it's not recomanded to have more than one container in a single Pod, but if somtimes you have to do so:
  # please refer to  multi-container Pod design patterns (e.g. sidecar, init and others)
    - name: wordpress # <- name of the container
      image: wordpress # <- the image to use,
      # you can specify anythink that a container accep such as command 
      command: ['sh', '-c', 'echo "Hello, Kubernetes!" && sleep 3600']
      entrypoint: # ...
```

you can apply the pod to k8s cluster using the following command.

`kubectl apply -f wordpress-pod.yaml`

# Creat Using Kubectl cli.
`kubectl run wordpress --image=wordpress --restart=Never`