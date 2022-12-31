# Break a string into multiline. Ansible ">" and "|" operators

There are two characters with what you can break lines
1. Literal Block Scalar "|"
2. Folded Block Scalar ">"

- Example
1. The example below will print mulit line with literals and folded it will joing. I have used with_itmes in order to save some lines
```
---
- name: Literal and folded block operators
  hosts: localhost
  vars:
    variable1: |
      This is line 1
      This is line 2
      This is line 3
    # Will print one long message
    variable2: >
      This is line 1
      This is line 2
      This is line 3
  tasks:
    - name: 
      ansible.builtin.debug:
        var: "{{ item }}"
      with_items:
        - variable1
        - variable2
```
NOTE: if you want to remove \n in the end to the execution becuase our output will print \n new line in the end. 
What you can do is
1. define "|-" 
2. define ">-"
3. use {{ variable1.split("\n") }}