# Check Logs

Inspect application or infrastructure logs for errors and anomalies.

## Arguments

- `$ARGUMENTS` — What to look for (e.g. "errors in last hour", "auth failures", "staging deploy logs")

## Instructions

1. Use Ansible inventory from `ansible/inventory/hosts.yaml` to identify target hosts.
2. Identify the relevant log source based on the request.
2. Search logs for:
   - Error and warning messages.
   - Stack traces and exceptions.
   - Unusual patterns or spikes.
   - The specific issue mentioned in the arguments.
4. Report findings:
   - Key error messages and their frequency.
   - Time range of the issue.
   - Affected services or endpoints.
   - Potential root cause.
5. Suggest next steps: investigate further, fix, or escalate.
6. Update your task with findings.
