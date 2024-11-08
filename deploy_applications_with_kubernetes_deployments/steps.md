## The Nautilus DevOps team is delving into Kubernetes for app management. One team member needs to create a deployment following these details:
## Create a deployment named `httpd` to deploy the application `httpd` using the image `httpd:latest` (ensure to specify the tag)

### To create a deployment named httpd that uses the httpd:latest image, you can use the following kubectl command:

###  Command to Create the Deployment

`kubectl create deployment httpd --image=httpd:latest`

This command will:

Create a deployment named `httpd`.
Use the `httpd:latest` image for the deployment.

### Verify the Deployment

To check if the deployment was created successfully, you can run:

`kubectl get deployments`

This will show the httpd deployment and its current status.

### Additional Notes

If you need to specify additional details (like `labels` or `replicas`), you can use a YAML file for more control. Here's an example YAML file:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: httpd
spec:
  replicas: 1
  selector:
    matchLabels:
      app: httpd
  template:
    metadata:
      labels:
        app: httpd
    spec:
      containers:
      - name: httpd
        image: httpd:latest
```
Save this file as httpd-deployment.yaml, and apply it with:

`kubectl apply -f httpd-deployment.yaml`

This YAML method is especially helpful if you want to customize the deployment further.
