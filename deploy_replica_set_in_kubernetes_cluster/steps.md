### The Nautilus DevOps team is gearing up to deploy applications on a Kubernetes cluster for migration purposes. A team member has been tasked with creating a ReplicaSet outlined below:
### Create a ReplicaSet using `nginx` image with `latest` tag (ensure to specify as `nginx:latest`) and name it `nginx-replicaset`.
### Apply `labels`: app as `nginx_app`, `type` as `front-end`.
### Name the container `nginx-container`. Ensure the replica count is `4`.
---

To create the required ReplicaSet for the Nautilus DevOps team's application migration, here is a YAML configuration file that you can use.

Save this as `nginx-replicaset.yaml` and apply it to the Kubernetes cluster.

```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-replicaset
  labels:
    app: nginx_app
    type: front-end
spec:
  replicas: 4
  selector:
    matchLabels:
      app: nginx_app
  template:
    metadata:
      labels:
        app: nginx_app
        type: front-end
    spec:
      containers:
      - name: nginx-container
        image: nginx:latest
```

### Explanation:

- `apiVersion`: `apps/v1` - Specifies the API version.
- `kind`: `ReplicaSet` - Specifies that this is a ReplicaSet resource.
- `metadata.name`: `nginx-replicaset` - Sets the ReplicaSet's name.
- `replicas`: `4` - Defines the number of pod replicas.
- `selector.matchLabels`: `app`: `nginx_app` - Ensures ReplicaSet targets pods with this label.
- `template.metadata.labels`: Labels the created pods with `app`: `nginx_app` and `type`: `front-end`.
- `containers`: Defines the container's name as `nginx-container` and the image as `nginx:latest`.

Applying the Configuration

To deploy the ReplicaSet, run:

`kubectl apply -f nginx-replicaset.yaml`

This command will create the ReplicaSet with the specified configuration and deploy 4 replicas of the nginx container on your Kubernetes cluster.
