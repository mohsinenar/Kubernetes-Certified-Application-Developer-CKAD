# Replication Controller 
ReplicationController used to creat replicates of a single pod to be always ready to use .

# Create a ReplicationController  using yaml

```yaml
apiVersion: v1 # <- ReplicationController are in v1
kind: ReplicationController # <- specify the kind
metadata: # <- first part of the file is to describe our ReplicationController 
  name: wordpress-replication-controller # <- unique name for the ReplicationController, should be unique in a namespace
  labels: # <- labels to tag the pod
    name: wordpress-replication # <- a list of key value pairs
spec: #<- second part to specify the desired state of our ReplicationController
    template: #<- since ReplicationController will create replicat of a pod we need to provide a tempale for the pod. all the bellow is the same a pod definition.
      metadata:
        name: wordpress-pod
        labels:
          version: v5
      spec:
        containers:
          - name: wordpress
            image: wordpress
    replicas: 3 # <- here we specify how many replicas we need from the template (the pod) we  want to be available all the time
```