# Ansible playbook

Ansible playbook is a configuration management tool that automates the configuration of systems and applications. It is written in the YAML format, which is a human-readable language that is easy to understand and write.

A playbook consists of a set of instructions, called tasks, that define the actions to be taken on managed nodes, or the systems being managed by Ansible. These tasks are organized into a series of plays, which are executed in a specific order.

Playbooks can be used to automate a wide range of tasks, such as installing software, configuring applications, and managing system services. They are an essential component of Ansible, as they allow users to automate complex tasks and processes in a structured, repeatable way.

To use an Ansible playbook, you need to have Ansible installed on your system, and you need to have access to the managed nodes. You can then run the playbook by using the ansible-playbook command.

## What are main components of the playbook
An Ansible playbook consists of several components, including:

- `Plays:` A play is a set of instructions that define the tasks to be executed on a group of managed nodes. A playbook can contain one or more plays, and each play specifies the host group to which it applies and the tasks to be performed.

- `Tasks:` A task is a single unit of work that defines an action to be taken on a managed node. Tasks are defined using module calls, which are pre-defined sets of instructions that can be used to perform a specific action.

- `Variables:` Variables are used to store values that can be used throughout a playbook. They can be used to store values such as hostnames, IP addresses, and other information that might change between different deployments.

- `Handlers:` Handlers are special tasks that are executed when notified by another task. They are often used to perform actions that need to be performed after a particular task has completed, such as restarting a service or sending an email notification.

- `Tags:` Tags are used to label tasks and plays in a playbook, allowing you to select specific tasks or plays to run when executing the playbook.

- `Conditions:` Conditions are used to specify when a task or play should be executed. They allow you to specify criteria that must be met in order for a task or play to be executed, such as the presence of a particular file or the value of a variable.

Overall, the main components of an Ansible playbook are used to define the tasks to be performed, the variables to be used, and the conditions under which the tasks should be executed. They allow you to automate complex processes and tasks in a structured, repeatable way.

# Lets check the following playbook
```
---
- name: example playbook
  hosts: localhos
  vars:
    myvar: "example text"
    mybool: true
    mycities:
      - Dubai
      - Paris

  tasks:
    - name: print variables task
      debug:
        var: "value {{ myvar }}"
      notify: reload

    - name: condition
      ansible.builtin.debug:
        msg: "example condition"
      when: mybool

    - name: Print cities
      ansible.builtin.debug:
        var: item
      loop: "{{ cities }}"

  handlers:
    - name: reload
      ansible.builtin.debug:            
        msg: "example handler"          
```
Task Explanation
- The playbook consists of three main sections:

- 1. The `name` and `hosts` sections:
<br> The name section specifies a human-readable name for the playbook, which in this case is `"example playbook"`.
<br> The `hosts` section specifies the host or group of hosts on which the tasks will be run. In this case, the tasks will be run on the local host.

- 2. The `vars` section:
<br> The `vars` section is used to define variables that can be used in the playbook. In this case, the playbook defines three variables:
<br> `myvar`: a string variable with the value `"example text"`
<br> `mybool`: a boolean variable with the value `true`
<br> `mycities`: a list variable containing two strings, `"Dubai"` and `"Paris"`

- 3. The `tasks` section:
<br> The `tasks` section contains a list of tasks to be executed by the playbook. Each task has a `name` and a set of actions to be performed, specified using the `ansible.builtin` module.
<br> In this playbook, there are three tasks:
    - 1) The first task is named `"print variables task"` and uses the `debug` module to print the value of the `myvar` variable. The `notify` keyword specifies that the task should trigger a handler when it finishes executing.
    - 2) The second task is named "condition" and uses the `debug` module to print the message "example condition". The `when` keyword specifies that this task should only be run if the value of the `mybool` variable is `true`.
    - 3) The third task is named `"Print cities"` and uses the `debug` module to print the value of each item in the `mycities` list. The `loop` keyword specifies that the task should be run once for each item in the list.
- 4. The handlers section:
<br> The `handlers` section contains a list of handlers that can be triggered by tasks. In this playbook, there is a single handler named `"reload"` that uses the `debug` module to print the message `"example handler"`. This handler will be triggered by the first task when it finishes executing.

- To execute playbook run
    ```
    ansible-playbook playbName.yml
    ```
- To validate the playbook for syntax check run 
    ```
    ansible-playbook --syntax-check example.yml
    ```
- To check stracture and organization of the playbook you can run
    ```
    ansible-playbook --list-task example.yml
    ```


