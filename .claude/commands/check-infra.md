# Check Infrastructure

Check the status of infrastructure and services.

## Arguments

- `$ARGUMENTS` — Optional: specific service or environment to check (e.g. "staging", "database", "redis")

## Instructions

1. Use Ansible inventory from `ansible/inventory/hosts.yaml` to identify target hosts.
2. Check the relevant infrastructure components:
   - Service health and uptime.
   - Resource utilization (CPU, memory, disk).
   - Database connectivity and performance.
   - External service dependencies.
   - SSL certificate expiry.
3. Check for recent alerts or anomalies.
4. Report using the infrastructure report format from `prompts/roles/devops.md`.
5. Flag anything that needs immediate attention.
6. Update your task with findings.
