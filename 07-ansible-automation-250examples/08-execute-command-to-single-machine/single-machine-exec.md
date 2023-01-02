# Execute command to only one HOSTNAME
Limit ansible playbook to only one machine. 
    
    1. use --limit at runtime
    2. hosts: HOSTNAME
    3. hosts: "{{ HOST }}    ===> Most advanced way how you can populate it

1. First option is easy and you do not have to midify the playbook
    ```
    --limit ====> usage: ansible-playbook --limit HOSTNAME PLAYBOOK
    ```
   Drawback you need to alwyas specify the hostname which is not usually reliable.

2. hosts: HOSTNAME in the ansible playbook which is more reliable to execute the playbook.
    ```
    Ansible Playbook
    ```
    Drawback is you need to remember everytime ansible code. You can execute against the unintended host

3. hosts: "{{ HOST }}" in the ansible playbook. This allow you to specify host or a group of hosts in the variable. May combine the execution of two previous options. And if you do not specify something nothing gonna happen which is more save. 
- In the example below is we defined built in variable {{ HOST }}
```
---
- name: execution test
  hosts: "{{ HOST }}"
  tasks:
    - name: execution test
      ansible.builtin.debug:
        msg: "execution test"
```
- Command to run is 
    ```
    ansible-playbook -i ../inventory.ini exec.yml -e "HOST=node2"
    ```
