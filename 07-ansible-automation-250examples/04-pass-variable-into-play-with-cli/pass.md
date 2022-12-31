# How to pass variables throug command line
You can pass variables to an Ansible playbook through the command line using the **`-e`** or **`--extra-vars`** option. This option allows you to specify variables in the form of `key=value` pairs, which will then be passed to the playbook at runtime.

- Some of the options on what you can pass as a argument:
```
--extra-vars "fruit=apple"   ===> name and value
--extra-vars '{"fruit":"apple"}'    ====> json format
--extra-vars "@file.json"          =====> json format
--extra-vars "@file.yml"           =====> yml file
```
- Lets see a simple example:
    - when you execute the following playbook default value will be apple 
    - But you can overwrite default value by setting extra variables in commald line
    - Command to set extra variables will be `ansible-playbook pass_vars.yml --extra-vars "fruit="banana" wich will overwrite default value
```
---
- name: Ansible variable demo
  hosts: localhost
  vars:
    fruit: "apple"
  tasks:
    - name: print message
      ansible.builtin.debug:
        msg: "fruit is {{ fruit }}"
```
- You can also create variable.yml file and pass different variables there
```
ansible-playbook pass_var.yml --extra-vars "@variables.yml"
```
- It will take -e argument equivalent of --extra-vars 
```
ansible-playbook pass_var.yml -e "@variables.yml"
```