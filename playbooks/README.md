# Playbooks

This directory holds top-level playbooks for patching and compliance workflows in this repository.

Available playbooks

- patch.yml
  - Rolling patch playbook that applies the `patching` role to hosts. Uses role defaults for parallelism (`patching_serial`) and failure tolerance (`patching_max_fail_percentage`).

- playbooks/remediate_compliance.yml
  - Detects and fixes common compliance issues (SSH hardening, auditd configuration, password aging). This playbook makes system changes and should be tested in staging before production.

- playbooks/generate_report.yml
  - Generates a simple compliance report by running a set of checks and printing a per-host summary.

Examples

- Run a rolling patch (25% at a time):

  ansible-playbook -i inventory/hosts.ini patch.yml

- Remediate compliance issues (dry-run first):

  ansible-playbook -i inventory/hosts.ini playbooks/remediate_compliance.yml --check

- Generate a compliance report:

  ansible-playbook -i inventory/hosts.ini playbooks/generate_report.yml

Notes
- Run ansible-lint and --syntax-check on these playbooks before executing them against production hosts.
