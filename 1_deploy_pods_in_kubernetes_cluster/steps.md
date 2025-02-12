## The Nautilus DevOps team is diving into Kubernetes for application management. One team member has a task to create a pod according to the details below: 
## Create a pod named `pod-httpd` using the `httpd` image with the `latest` tag. 
## Ensure to specify the tag as `httpd:latest`. Set the app label to `httpd_app`, and name the container as `httpd-container`.

### To create the Kubernetes pod as specified, follow these steps. You can create a YAML configuration file for the pod.

1. Create a file named `pod-httpd.yaml` with the following content:

```
apiVersion: v1
kind: Pod
metadata:
  name: pod-httpd
  labels:
    app: httpd_app
spec:
  containers:
    - name: httpd-container
      image: httpd:latest
      ports:
        - containerPort: 80
```
2. Apply the configuration:

`kubectl apply -f pod-httpd.yaml`

3. Check Pod Status

`kubectl get pods`

