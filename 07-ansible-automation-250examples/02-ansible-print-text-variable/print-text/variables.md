# How to print text/variable during execution. Ansible debg module

- The `debug` module is an Ansible module that allows you to print messages or the values of variables during the execution of a playbook or role. It is often used for debugging purpose, as it allows you to see the intermediate steps and variables in your playbook as it is being executed.

Example for `debug` module
```
- name: Print a message
  debug:
    msg: "This is a message"
```
- If you want to pring variable you can use the following syntax
```
- name: Print the values of variable
  debug:
    var: my_variable
```

### Prameters
1. msg (string)  ===> "Hello world" / customized message
2. var (string)  ===> variable name
3. verbosity (integer) ===> 0-3

### Demo with ansible debug module
- print "Hello world"
- print a text
- print a variable
- print text and variable
- verbosity level

Examples:
- 1. If you do not specify nothing it will print "Hello world"
```
---
- name: Debug module demo
  hosts: localhost
  vars:
    fruit: "apple"
  tasks:

    # If not speicfied any message it will print hello world
    - name: Debug message
      debug:
    
    # Print the message content with debug module
    - name: Print debug message
      ansible.builtin.debug:
        msg: "This is debug message content"

    # Print debug message with variable
    - name: Print variable with debug
      debug:
        var: fruit

    # Print the value of the message in the content with verbosity
    - name:
      ansible.builtin.debug:
        msg: "I like eating {{ fruit }}"
        verbosity: 3
```
1. First task prints Hello world since that is the default value if message is not specified
2. Secod task prints content for debug module with the content
3. Third task prints variable conent defined in vars above
4. Fourth task prints content of the variable in the verbose mode

### Another Example of debug module usage is:
- This plauybook will run when there is specific conidtions are met
```
- name: Print the value of a variable
  debug:
    var: my_variable
  when: role_debug
```
- One more example for debug module is to run it with loop:
```
- name: Print a message for each item in a list
  debug:
    msg: "Processing item {{ item }}"
  with_items:
    - item1
    - item2
    - item3
```

