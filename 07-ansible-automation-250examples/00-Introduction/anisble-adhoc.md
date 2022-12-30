# Ad-hoc commands
Ansible ad-hoc commands are one-time commands that allow users to quickly perform a specific task on one or more managed hosts. These commands do not require the creation of a playbook and can be run directly from the command line
- Some of the examples for ad-hoc commands are
1. To ping host, 
```
ansible all -m ping
```
- The `"ansible all"` portion of the command specifies that the command should be run on all managed hosts.
- The `"-m ping"` portion of the command specifies that the "ping" module should be used. The "ping" module is a built-in Ansible module that sends a simple request to the managed host to check if it is reachable and responding.

2. Installing packages on all managed hosts:
```
ansible all -m yum -a "name=httpd state=present"
```
- The `"ansible all"` portion of the command specifies that the command should be run on all managed hosts.
- The `"-m yum"` portion of the command specifies that the "yum" module should be used. The "yum" module is a built-in Ansible module that allows users to manage packages on systems that use the "yum" package manager (such as Red Hat, CentOS, and Amazon Linux).
- The `"-a "name=httpd state=present"` portion of the command specifies the arguments for the "yum" module. The "name=httpd" argument specifies the name of the package to be installed, and the "state=present" argument specifies that the package should be installed if it is not already present on the system.
- When this command is run, Ansible will connect to all managed hosts and check if the "httpd" package is already installed. If the package is not installed, it will be installed using the "yum" package manager. If the package is already installed, no action will be taken.

3. Gather information about all managed hosts
```
ansible all -m setup
```
4. To check size
```
ansible -all -a "df -h"
```
5. Copying a file to all managed hosts:
```
ansible all -m copy -a "src=local_file.txt dest=/path/on/remote/host"
```
6. Restarting a service on all managed hosts:
```
ansible all -m service -a "name=httpd state=restarted"
```