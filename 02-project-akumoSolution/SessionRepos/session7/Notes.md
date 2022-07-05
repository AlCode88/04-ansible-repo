<h1><b>Session Tasks</b></h1>

<b>Tasks 1:</b>
Define a yaml format inventory. Create a group called "prod" in your inventory file. Write a playbook that pings servers, only if "prod" group is defined in inventory.yaml

<b>Tasks 2:</b>
Write the playbook that copies /tmp/tesfile from localhost to Ubuntu only serever /tmp defined in inventory file. If it doesnt exist create the file.

Note: We are going to copy the file from our local mac machine- <b> scp /tmp/testfile root@ ip of the server :/tmp </b>. 

<b>Tasks 3:</b>
write a playbook change the permission on /tmp/testfile in localhost to read/write for everyone condition: server OS is CentOS

<b>Tasks 4:</b>
To run on remote server (Ubuntu), and change the file permission on /tmp/testfile
condition: hostname = ubuntu

<b>Tasks 5:</b>
Create a group in inventory file, called “dev” add centos under dev group write a playbook that pings the CentOS servers, only if dev group is defined in inventory.

<b>Tasks 6:</b>
Write a playbook that copies file from remote server Ubunutu to localhost uder /root. Condition: remote server distribution should be Ubuntu and hostname should be ubuntu

<b>Tasks 7:</b>
Write a playbook that pings all servers, only if the 'prod' is defined in inventory file. The playbook also installs vim, wget and curl packages in remote hosts. The following users needs to be added on servers with distribution "CentOS". - amy, anna, liza The playbook also generates ssh keys for all users.

- By default there is two groups "all" and "ugroupped".

- ansible --list-host -i inventory.yaml all --- will list you the all available hosts in that you have with the contorol node and if you want to check it by group name you can run the following command ansible --list-host -i inventory.yaml ungroupped or it can be prod or dev as well.

there is a defult varibales that ansible stores in the memory. For example "group_name" 

<u>ITTERATIVE APPROACH :</u> small chuncks of code but run often and this method comes from agile method.

<u>ITERATION :</u> is the timeframe three iterations and some companies define the itteration as a "sprint" which is usually two weeks.

<u>WATER FALL APPROACH:</u> large chuncks of codes run not often once in a while.

<u>Upstream jobs</u> - 

<u>Upstream jobs</u> -

FETCH - This module works like copy, but in reverse. It is used for fetching files from remote machines and storing them locally in a file tree, organized by hostname. Files that already exist at dest will be overwritten if they are different than the src. This module is also supported for Windows targets.

<u>"{{ item }}</u> makes Looping and we need to define it with_items producing looping.

