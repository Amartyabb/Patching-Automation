# Patch all servers with rolling updates (25% at a time)
ansible-playbook -i inventory/hosts.ini patch.yml

# Patch only web servers with security updates
ansible-playbook -i inventory/hosts.ini patch.yml \
  --limit web_servers \
  -e "patching_security_only=true"

# Dry run supported tasks before applying updates
ansible-playbook -i inventory/hosts.ini patch.yml --check
