# Install / Uninstall Nginx on Ubuntu and RHEL

### install-nginx.yml

Use the `install-nginx.yml` playbook to install Nginx web server on Ubuntu or RHEL based systems. It uses `install-nginx` role and:

- automates the installation
- copies index.html with owner and permissions
- allows port 80 through ufw and firewalld
- starts and enables nginx to run on boot.

```bash
ansible-playbook install-nginx.yml
```

---

### uninstall-nginx.yml

Use the `uninstall-nginx.yml` playbook to undo the changes made by `install-nginx.yml` playbook. It uses `uninstall-nginx` role and:

- stops and disables nginx service
- removes nginx package
- removes index.html file
- removes firewall rules allowing port 80 through ufw and firewalld

```bash
ansible-playbook uninstall-nginx.yml
```

---
