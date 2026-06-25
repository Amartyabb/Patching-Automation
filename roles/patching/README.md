# Patching role

This role performs OS package updates in a rolling manner with optional pre- and post-checks.

Files of interest
- defaults/main.yml - Role variables (patching_reboot_enabled, patching_reboot_timeout, patching_pre_check_enabled, patching_post_check_enabled, patching_security_only, patching_serial, patching_max_fail_percentage, patching_health_url, patching_health_retries, patching_health_delay)
- tasks/main.yml - Main patch workflow (includes pre_checks.yml and post_checks.yml)
- tasks/pre_checks.yml - Pre-patching validations (disk space, running services, kernel)
- tasks/post_checks.yml - Post-patching validations (system status, failed services, app health, kernel) and report generation

How to use

- Run the rolling patch playbook in the repo root:

  ansible-playbook -i inventory/hosts.ini patch.yml

- Override variables on the command line, for example:

  ansible-playbook -i inventory/hosts.ini patch.yml -e "patching_security_only=true"

Notes
- The role writes a patching report to /var/log/patching-report-<date>.txt. Ensure your target hosts are writable there.
- For application-level verification, set patching_health_url to a reachable endpoint.
