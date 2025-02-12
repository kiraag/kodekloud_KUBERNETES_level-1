## The Nautilus DevOps team is planning to deploy some micro services on Kubernetes platform. The team has already set up a Kubernetes cluster and now they want to set up some namespaces, deployments etc. Based on the current requirements, the team has shared some details as below:
## Create a namespace named `dev` and deploy a `POD` within it. Name the pod `dev-nginx-pod` and use the `nginx` image with the `latest` tag. Ensure to specify the tag as `nginx:latest`.

### To create a namespace named `dev` and then deploy a pod named `dev-nginx-pod` within it using the `nginx:latest` image, follow these steps:

### Step 1: Create the Namespace

Run the following command to create the dev namespace:

`kubectl create namespace dev`

### Step 2: Deploy the Pod in the dev Namespace

Now, create the `dev-nginx-pod` in the `dev` namespace using the `nginx:latest` image. You can do this with a kubectl command or a YAML file.

#### Option 1: Direct Command

Use this command to create the pod directly in the dev namespace:

`kubectl run dev-nginx-pod --image=nginx:latest --restart=Never -n dev`

This command:

Creates a pod named `dev-nginx-pod`.
Uses the `nginx:latest` image.
Deploys it in the `dev` namespace.

#### Option 2: YAML Configuration

Alternatively, create a YAML file for more control.

Create a file named `dev-nginx-pod.yaml` with the following content:

```
apiVersion: v1
kind: Pod
metadata:
  name: dev-nginx-pod
  namespace: dev
spec:
  containers:
    - name: nginx
      image: nginx:latest
```

Apply the YAML file:

`kubectl apply -f dev-nginx-pod.yaml`

### Step 3: Verify the Namespace and Pod

Check if the namespace was created:

`kubectl get namespaces`

Check the pod status within the dev namespace:

`kubectl get pods -n dev`

This will confirm that `dev-nginx-pod` is running in the `dev` namespace.