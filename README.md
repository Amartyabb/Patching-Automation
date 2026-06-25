# Patching-Automation

This repository provides Ansible roles and playbooks to:

- Perform rolling OS package patching with pre-/post-checks
- Validate network/firewall compliance
- Remediate common compliance issues
- Generate simple compliance reports

Getting started

1. Review docs/RUNNING.md for basic run examples.
2. Validate the playbooks with linting and syntax checks:

   ansible-lint .
   ansible-playbook --syntax-check patch.yml

3. Test in a staging environment, then run against production inventories.

Contributing

If you want to change behavior or add tests, consider opening a branch and a pull request. CI and molecule tests are recommended for changes that affect role behavior.
