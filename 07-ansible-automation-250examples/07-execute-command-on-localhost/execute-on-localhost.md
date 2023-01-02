# Execute command on local machine
- There are 3 ways to execute command on localhost
    
    1. connection plugin  ===> Will apply at ansible play level. Best way.
    2. delegate_to: localhost  ===> task level
    3. local_action ===> Use this as a last alternative but connection plugin will be safficient

    Example:
    ```
    ---
    - name: localhost demo
      hosts: localhost
      vars:
        ansible_connection: local
        ansible_python_interpreter: "{{ ansible_playbook_python }}"
    
      tasks:
        - name: print hostanme
          ansible.builtin.debug:
            msg: "{{ inventory_hostname }}"
    ```
The "hosts: localhost" line specifies that the tasks in this playbook should be run on the local machine.

The "vars" section defines two variables that are used in the playbook. The "ansible_connection: local" variable specifies that the tasks should be run locally, rather than connecting to a remote machine over SSH. The "ansible_python_interpreter" variable specifies the python interpreter that should be used to run the tasks.

The "tasks" section contains a single task, which is to print the hostname of the local machine. This task uses the "ansible.builtin.debug" module to print a message, which in this case is the "inventory_hostname" variable. This variable is a built-in Ansible variable that contains the hostname of the current machine.

- ansible_python_interpreter: "{{ ansible_playbook_python }}"
   This line of code specifies the python interpreter that should be used to run the tasks in the playbook. The "ansible_python_interpreter" variable is set to the value of the "ansible_playbook_python" variable, which is an Ansible built-in variable that contains the path to the python interpreter that was used to run the ansible-playbook command.
   
   By using the "ansible_playbook_python" variable, the playbook ensures that it uses the same python interpreter as the one used to run the ansible-playbook command. This can be useful if the playbook needs to use specific python modules or if the system has multiple python versions installed and you want to ensure that the correct version is used.