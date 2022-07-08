# Getting Started with ansible

1. Install Ansible on control mode
2. Swithch to Ansible user to make the key
`sudo su - ansible`
3. Generate SSH keys for ansible user
`ssh-keygen` So we copy the control nodes ssh keys to slaves.
4. Copy your keys to ansible nodes with
`ssh-cpoy-id node1` and `ssh-cpoy-id node2`
5. Create an inventory in `vim /home/ansible/inventory`. Add node1 and node2
6. We need to add ansible to Sudoers group in node1 and node2 in slaves, so That Ansible could perform some tasks without any password request.
7. Connect to the node1 and node2 and run `sudo visudo` command and start to edit `sudoers file` you can add ansible user to wheels group or you can just modify wheels group
8. Verify that it is pingable with command `ansible -i /home/ansible/inventory node1 -m ping` and
`ansible -i /home/ansible/inventory node2 -m ping`
9. 