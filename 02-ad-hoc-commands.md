# Ad-Hoc Commands

### Check Whether Ansible Is Working Correctly

```bash
ansible localhost -m ping
```

---

### List All Hosts From The Inventory File

```bash
ansible-inventory -i 01-inventory.ini --graph
```

---

### Ping Module

```bash
# ping all hosts in rhel group
ansible -i 01-inventory.ini rhel -m ping

# ping specific host (r1) in the inventory file
ansible -i 01-inventory.ini tharindu@r1 -m ping

# ping all hosts in ubuntu group
ansible -i 01-inventory.ini ubuntu -m ping

# ping all hosts in the inventory file
ansible -i 01-inventory.ini all -m ping
```

---

### Shell Module

```bash
# check uptime
ansible -i 01-inventory.ini all -m shell -a 'uptime -p'

# check who is logged in
ansible -i 01-inventory.ini all -m shell -a 'who'

# check connectivity to google.com
ansible -i 01-inventory.ini all -m shell -a 'ping -c 4 google.com'

# reboot all hosts
ansible -i 01-inventory.ini all -m shell -b -a 'reboot'
```

---

### Copy Module

```bash
# copy a file from control node to managed nodes with specific permissions
ansible -i 01-inventory.ini all -m copy -b -a 'src=~/hello.txt dest=~/hello.txt mode=0644 owner=tharindu group=tharindu'
```

### File Module

```bash
# create a file with permissions and ownership
ansible -i 01-inventory.ini all -m file -a 'path=~/test.txt mode=0644 owner=tharindu group=tharindu state=touch'

# create a directory (just like `mkdir -p`) with permissions and ownership
ansible -i 01-inventory.ini all -m file -a 'path=~/mainDir/subDir mode=0755 owner=tharindu group=tharindu state=directory'

# remove a file or directory (just like `rm -rf`)
ansible -i 01-inventory.ini all -m file -a 'path=~/mainDir state=absent'
ansible -i 01-inventory.ini all -m file -a 'path=~/test.txt state=absent'
```

---

### APT & DNF Modules

```bash
# install nginx on ubuntu group
ansible -i 01-inventory.ini ubuntu -b -m apt -a 'name=nginx state=latest update_cache=true'

# uninstall httpd on ubuntu group
ansible -i 01-inventory.ini ubuntu -b -m apt -a 'name=nginx state=absent'

# autoremove unused packages on rhel group
ansible -i 01-inventory.ini rhel -b -m dnf -a 'autoremove=true'

```

### User Module

```bash
# create a user
# mkpasswd -m sha-512
ansible -i 01-inventory.ini all -b -m user -a 'name=devuser password=<HASHED_PASSWORD>'

# delete a user
ansible -i 01-inventory.ini all -b -m user -a 'name=devuser state=absent'
```

### Service Module

```bash
ansible -i 01-inventory.ini all -b -m service -a 'name=nginx state=started enabled=true'

ansible -i 01-inventory.ini all -b -m service -a 'name=nginx state=stopped enabled=false'

ansible -i 01-inventory.ini all -b -m service -a 'name=nginx state=restarted'
```

### Setup Module

```bash
# gathering facts
ansible -i 01-inventory.ini all -m setup
```
