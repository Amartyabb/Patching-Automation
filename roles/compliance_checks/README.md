# Compliance checks role

This role contains checks to validate host compliance (network/firewall and other checks). It is intended to be used by playbooks that either report or remediate compliance issues.

Files of interest
- tasks/network.yml - Network & firewall checks (UFW status and listening ports)

Variables
- prohibited_ports: list of ports that must NOT be listening (defaults: [23, 21, 69])

How to run the checks

Include the role or the specific task file in a playbook, for example:

- name: Run compliance network checks
  hosts: all
  roles:
    - { role: compliance_checks }

Or run the task directly:

ansible-playbook -i inventory/hosts.ini -e "prohibited_ports=[23,21,69]" playbooks/generate_report.yml

Notes
- The role uses assert tasks; failing assertions will cause the play to fail. Use --check for dry-run verification where appropriate.
