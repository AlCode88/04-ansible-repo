# Copy and Template modules
1. Copy module ===> It deals with whitespace and newlines.
2. Template module ===> For advanced formatting of if content contains a variable, use the `ansible.builtin.template` module

The copy and template modules in ansible are both used to transfer files to the remote host. However, they differ in how they handle the content of the file being transferred.

The copy module is used to transfer a local file as-is to the remote host. It does not perform any modifications or substitutions on the file content. For example, you could use the copy module to transfer a local script file to the remote host like this:
```
- name: Transfer script file
  copy:
    src: /path/to/local/script.sh
    dest: /path/to/remote/script.sh
```
The template module, on the other hand, is used to transfer a local file and perform variable substitutions on its content before transferring it to the remote host. This allows you to customize the content of the file based on variables defined in your playbook or host facts. For example, you could use the template module to transfer a local configuration file to the remote host and substitute variables like this:
```
- name: Transfer configuration file
  template:
    src: /path/to/local/config.tmpl
    dest: /path/to/remote/config
  vars:
    database_name: mydatabase
    database_user: myuser
```
In this example, the template module will substitute any occurrences of the variables "database_name" and "database_user" in the local configuration file with the corresponding values defined in the "vars" section. The resulting file will then be transferred to the remote host.

In summary, the main difference between the copy and template modules is that the copy module transfers a file as-is, while the template module performs variable substitutions on the file before transferring it.