# Shell vs Command
1. Command 
    - ===> executes commands without using target shell. Bash,zshell, etc are avoided. 
    - Returns changed status.
    - Defula module for ansible.
    - Can only execute binaries available on the remote host
    - Will not be impacted local shell variable since it bypasses shell
2. Shell 
    - ===> executes all shell features in the system. 
    - Returns changed status.
    - More dangerous than command
    - You can use pipes and % and colum you do not need shell module
The main difference between the shell and command modules in Ansible is how they execute commands on the remote host.

The `shell module` allows you to execute commands using a `shell interpreter, such as bash or zsh`. This allows you to use `shell-specific features and operators, like pipes and redirection`, in your commands. For example, you could use the shell module to run a command like this:

```
- name: Run command using shell
  shell: ls -l /tmp | grep test | awk '{print $9}'
```
The `command module`, on the other hand, does not use a shell interpreter and only allows you to run simple commands. It `does not support shell-specific features` or operators. For example, you could use the command module to run a command like this:
```
- name: Run simple command
  command: ls -l /tmp
```
The `shell module is generally considered more dangerous than the command module` because it allows you to execute arbitrary code on the remote host. This means that if you are not careful, you could potentially run malicious commands or inadvertently cause damage to the system. The `command module`, on the other hand, is more restricted and can only `run simple commands`, so it is less likely to cause problems.

In general, it is recommended to use the `command module` whenever possible and only use the shell module when necessary. This helps to minimize the risk of unintended consequences and keeps your playbook more secure.

Example: 
```
---
- name: command module example
  hosts: all
  tasks:
    - name: check uptime
      ansible.builtin.command: uptime
      register: command_output
    
    - name: coammand output
      ansible.builtin.debug:
        var: command_output.stdout_lines
    
    - name: shell example
      ansible.builtin.shell: cat /etc/os-release | grep -Ei "^Name" | sed 's/[\\"]//g'
      register: command_output
    
    - name: Display command
      ansible.builtin.debug:
        var: command_output.stdout_lines

    - name: Shell example. You can not use * with command
      shell: "ls -la *"
      register: command_output

    - name: Display message on the screen
      debug:
        var: command_output.stdout_lines
```
In the given ansible playbook, the variable "command_output.stdout_lines" is a list of strings that contains the output of the "uptime" command.

The "command_output" variable is a dictionary that contains various properties of the command execution, including the standard output, standard error, and exit code. The "stdout_lines" property is a list of strings that represents the standard output of the command, with each line of output being a separate element in the list.

The "debug" module is then used to print the contents of the "command_output.stdout_lines" variable to the console. This allows you to see the output of the "uptime" command as a list of strings.

For example, if the "uptime" command returns the following output:
```
 13:14:01 up 10 days,  4:27,  0 users,  load average: 0.00, 0.00, 0.00
```
Then the "command_output.stdout_lines" variable will contain a single element in the list: "13:14:01 up 10 days, 4:27, 0 users, load average: 0.00, 0.00, 0.00". This element can then be accessed and manipulated as needed in subsequent tasks in the playbook.