# Install Nginx on Ubuntu and RHEL

### This Role:

- installs Nginx web server on Ubuntu and RHEL based systems
- copies index.html with owner and permissions to the servers
- allows port 80 through ufw and firewalld
- starts and enables nginx to run on boot.

---

### Check Results:

- Access the web server using the server's IP address in a web browser.
- You should see the content of the `index.html` file that was copied to the server.
- You can also check using the command:
  ```bash
  sudo systemctl status nginx
  netstat -ntpl | grep :80
  curl -I http://IP_ADDRESS
  ```

---
