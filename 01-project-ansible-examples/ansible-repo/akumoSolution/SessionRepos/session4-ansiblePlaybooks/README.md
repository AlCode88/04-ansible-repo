Playbook Tasks

1) Task 1 :
a) Add a new server in DigitalOcean
  - OS = Ubuntu latest
  - Add SSH Key of Ansible Server
  - Hostname = ubuntu

b) Add one more server in DigitalOcean
  - OS = CentOS 7.6
  - Add SSH Key of Ansible Server
  - Hostname = centos

c) Create an inventory file called 'dev-inventory.yaml' under development folder.
  - add both hosts under group called 'dev' in your inventory
  - ping 'dev' group, make sure ping is successful

Task 2 :
Write a playbook called ‘ping.yml’. The playbook should ping dev servers only.
So we will create a ping.yaml file and we will write a playbook to ping dev group only. 

Task 3 :
Write a playbook that runs 'df -h' on remote hosts, call it ‘diskusage.yml' The playbook should run on all servers

Task 4 :
Write a playbook that check free memory of the remote hosts, call it ‘memorycheck.yml’. Run the playbook on dev servers only. 

Task 5 :
Create a file called index.html under /tmp folder of localhost.
Content:
<!DOCTYPE html>
<html>
<head>
        <title>This is my Page !</title>
</head>
<p> Ansible is Fun 1 </p>
</html>
Write a playbook called 'copy.yml', the playbook should copy a file from localhost to remote hosts.
Run the playbook on centos server.
Copy destination = /tmp

Task 6 :
Write a playbook that installs apache on Redhat/Centos servers, call it httpd.yml. Run  the playbook on centos server.