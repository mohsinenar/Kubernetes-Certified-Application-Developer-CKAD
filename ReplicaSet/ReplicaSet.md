# ReplicaSet

A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time. As such, it is often used
to guarantee the availability of a specified number of identical Pods.

# Creating ReplicaSet using yaml.

```yaml
apiVersion: apps/v1 # <-- ReplicaSet are available in apps/v1
kind: ReplicaSet
metadata:
  name: wordpress-replicaset  <- unique name for the ReplicaSet, should be unique in a namespace
  labels:
    name: wordpressreplicaset
spec: <- we specify here the desired state of the ReplicaSet
  replicas: 3
  template: # <- the template is used by the ReplicaSet to create new pods to match the required number of replicas. 
    # the template is the same as a pod definition
    metadata:
      name: wordpress-pod
      labels:
        name: wordpress
    spec:
      containers:
        - name: wordpress
          image: wordpress
  selector: <-- selectors are used by the replicas set to watch the availble pods so it can create new pods then the number of availble pods does not match the desired number.
    matchLabels:
      name: wordpress
    matchExpressions:
      - key: 
        operator: 

```