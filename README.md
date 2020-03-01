# Welcome to Ansible Ad-hoc

## Introduction to ad-hoc commands

An Ansible ad-hoc command uses the /usr/bin/ansible command-line tool to automate a single task on one or more managed nodes. Ad-hoc commands are quick and easy, but they are not re-usable. So why learn about ad-hoc commands first? Ad-hoc commands demonstrate the simplicity and power of Ansible. The concepts you learn here will port over directly to the playbook language

### Why use ad-hoc commands?

Ad-hoc commands are great for tasks you repeat rarely. For example, if you want to power off all the machines in your lab for Christmas vacation, you could execute a quick one-liner in Ansible without writing a playbook. An ad-hoc command looks like this:

    $ ansible [pattern] -m [module] -a "[module options]"
    
### 1.Setup Module

To get information about the network or hardware or OS version or memory related information the setup module will help to gather the same about the target machines. On the control, the machine runs the below command.

    $ anisble web -m setup 
    
### 2. Command Module

The default module for the ansible command-line utility is the command module. You can use an ad-hoc task to call the command module and reboot all web servers in Atlanta, 10 at a time. Before Ansible can do this, you must have all servers in Atlanta listed in a a group called [atlanta] in your inventory, and you must have working SSH credentials for each machine in that group. To reboot all the servers in the [atlanta] group:

    $ ansible atlanta -a "/sbin/reboot"

By default Ansible uses only 5 simultaneous processes. If you have more hosts than the value set for the fork count, Ansible will talk to them, but it will take a little longer. To reboot the [atlanta] servers with 10 parallel forks:

    $ ansible atlanta -a "/sbin/reboot" -f 10

/usr/bin/ansible will default to running from your user account. To connect as a different user:

    $ ansible atlanta -a "/sbin/reboot" -f 10 -u username

Rebooting probably requires privilege escalation. You can connect to the server as username and run the command as the root user by using the become keyword:

    $ ansible atlanta -a "/sbin/reboot" -f 10 -u username --become [--ask-become-pass]

If you add --ask-become-pass or -K, Ansible prompts you for the password to use for privilege escalation (sudo/su/pfexec/doas/etc).

Some of the Examples are given below
 
   $ ansible atlanta –m command -a ‘uptime’
   $ ansible atlanta –m command -a ‘hostname’

