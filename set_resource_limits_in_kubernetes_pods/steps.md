## The Nautilus DevOps team has noticed performance issues in some Kubernetes-hosted applications due to resource constraints. To address this, they plan to set limits on resource utilization. Here are the details:
## Create a pod named `httpd-pod` with a container named `httpd-container`. Use the `httpd` image with the `latest` tag (specify as `httpd:latest`). Set the following `resource limits`:                                                                                                                           `Requests: Memory: 15Mi, CPU: 100m                                                                                                                         Limits: Memory: 20Mi, CPU: 100m`

### To create a pod with specific resource requests and limits, you can use a YAML configuration file. Here’s how to configure httpd-pod with the specified resource constraints.

#### Step 1: Create the YAML File

Create a file named httpd-pod.yaml with the following content:

```
apiVersion: v1
kind: Pod
metadata:
  name: httpd-pod
spec:
  containers:
    - name: httpd-container
      image: httpd:latest
      resources:
        requests:
          memory: "15Mi"
          cpu: "100m"
        limits:
          memory: "20Mi"
          cpu: "100m"
```

This configuration specifies:

* The pod name as `httpd-pod`.
* The container name as `httpd-container`.
* The image `httpd:latest`.
* Resource requests (minimum guaranteed resources) for memory (15Mi) and CPU (100m).
* Resource limits (maximum allowed resources) for memory (20Mi) and CPU (100m).

#### Step 2: Apply the YAML Configuration

Apply this configuration with the following command:

`kubectl apply -f httpd-pod.yaml`

#### Step 3: Verify the Pod and Resource Limits

To confirm that the pod is created with the correct resource limits, use:

`kubectl get pod httpd-pod -o yaml`

Or, you can describe the pod for a more readable output:

`kubectl describe pod httpd-pod`

This will display the details, including the resource requests and limits, confirming that the configuration was applied successfully.