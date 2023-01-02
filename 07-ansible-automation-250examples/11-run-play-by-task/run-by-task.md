# How to run playbook by task. How to use tag statement in ansible.
Tags in ansible playbooks are used to label and group tasks. They allow you to selectively run specific tasks or groups of tasks in a playbook, rather than running all tasks in the playbook. 

### Some parameters to specify tags. 
```
--tags all                ===> to specify all tags
--tags tag1               ===> to specify only one tag
--tags 'tag1','tag2'       ===> to specify list of tags
--skip-tags [tag3, tag4]  ===> to skip list of tags
--tags tagged             ===> to specify tagged
--tags untagged           ===> to specify untagged
```

Troubleshooting suggestions on tag
1. The "--tags" option should be followed by a comma-separated list of tags, not another "--tags" option. The correct syntax would be "--tags tag1,tag2,tag3".

2. The list of tags is surrounded by brackets "[ ]" instead of quotes "". This will cause the command to fail as the brackets are not a valid syntax for specifying tags. The correct syntax would be "--tags 'tag1,tag2,tag3'".

3. The tags are not properly quoted, which may cause problems if any of the tags contain spaces or special characters. The correct syntax would be "--tags 'tag1','tag2','tag3'".

