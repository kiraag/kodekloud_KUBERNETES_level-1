## An application currently running on the Kubernetes cluster employs the nginx web server. The Nautilus application development team has introduced some recent changes that need deployment. They've crafted an image `nginx:1.19` with the latest updates.

## Execute a rolling update for this application, integrating the `nginx:1.19` image. The deployment is named `nginx-deployment`.     Ensure all pods are operational post-update.
---

To execute a rolling update on the `nginx-deployment` using the new `nginx:1.19` image, follow these steps:

### Step 1: Check the Current Status of the Deployment

Verify the current image version and the status of the deployment.

`kubectl get deployment nginx-deployment -o wide`

### Step 2: Update the Deployment to Use the New Image

Use the kubectl set image command to update the nginx-deployment to the new image version nginx:1.19.

`kubectl set image deployment/nginx-deployment <container-name>=nginx:1.19`

### Step 3: Monitor the Rolling Update

To monitor the progress of the update and ensure that all pods are updated without downtime, use the following command:

`kubectl rollout status deployment/nginx-deployment`

This will show the status of the rollout, allowing you to verify that all pods are gradually updated to the new image.

### Step 4: Confirm All Pods Are Running

After the update completes, confirm that all pods are running the new image and are in the "Running" status.

`kubectl get pods`

### Step 5: Verify the Image Version

Finally, double-check that the image version is updated in all pods:

`kubectl describe deployment nginx-deployment | grep "Image"`

This completes the rolling update.