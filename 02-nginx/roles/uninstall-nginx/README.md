# Uninstall Nginx on Ubuntu and RHEL

### This Role:

- stops and disables nginx from running on boot.
- uninstalls Nginx web server on Ubuntu and RHEL based systems
- removes index.html from the servers
- denies port 80 through ufw and firewalld

---

### Check Uninstallation:

- Access the web server using the server's IP address in a web browser.
- You should not see the content of the `index.html` file that was copied to the server.
- You can also check using the command:
  ```bash
  sudo systemctl status nginx
  netstat -ntpl | grep :80
  curl -I http://IP_ADDRESS
  ```

---
