# Deploy

Run a deployment to the specified environment.

## Arguments

- `$ARGUMENTS` — Target environment (e.g. "staging", "production")

## Instructions

1. **Pre-deploy checks:**
   - Verify all tests pass on the branch being deployed.
   - Check that the target environment is healthy (`/check-infra`).
   - Confirm the deployment target with the user if it's production.
2. **Deploy:**
   - Use Ansible playbooks from `ansible/playbooks/` with inventory from `ansible/inventory/hosts.yaml`.
   - Run the appropriate playbook for the target environment.
   - Monitor the deployment for errors.
3. **Post-deploy checks:**
   - Verify the service is healthy after deployment.
   - Run smoke tests if available.
   - Check logs for errors (`/check-logs`).
4. Report the deployment result: success or failure with details.
5. If deployment fails, roll back and report what went wrong.
6. Update your task and document in `knowledge/runbooks/` if this is a new procedure.
