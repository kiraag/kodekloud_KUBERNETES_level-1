### Earlier today, the Nautilus DevOps team deployed a new release for an application. However, a customer has reported a bug related to this recent release. Consequently, the team aims to revert to the previous version.
### There exists a deployment named `nginx-deployment`; initiate a rollback to the previous revision.
---
To roll back the `nginx-deployment` to its previous revision, you can use the `kubectl rollout undo` command. Here’s how to do it:

1. Check the Current Rollout History: This step is optional but can be helpful to confirm the deployment history before rolling back.

`kubectl rollout history deployment/nginx-deployment`

This command will show the revision history of `nginx-deployment`, indicating previous versions.

2. Initiate the Rollback: Use the following command to rollback the deployment to the previous revision:

`kubectl rollout undo deployment/nginx-deployment`

By default, this command reverts the deployment to the most recent previous revision.

3. Verify the Rollback: After rolling back, check the status to ensure the rollback was successful:

`kubectl rollout status deployment/nginx-deployment`

This will show whether the rollback has been applied correctly and if the deployment is running without issues.

4. Confirm the Current Revision: If needed, you can confirm the current revision by checking the rollout history again:

`kubectl rollout history deployment/nginx-deployment`

This will confirm that the rollback to the previous version has been successfully applied.

## Optional

If you need to roll back the deployment by more than one step, you can specify the target revision directly using the `--to-revision flag`.

- Roll Back to the Specific Revision: Use the following command, specifying the revision number from two steps back:

`kubectl rollout undo deployment/nginx-deployment --to-revision=3` (you can choose the revision number as your requirement)


