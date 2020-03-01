# Welcome to Ansible Ad-hoc

## Introduction to ad-hoc commands

An Ansible ad-hoc command uses the /usr/bin/ansible command-line tool to automate a single task on one or more managed nodes. Ad-hoc commands are quick and easy, but they are not re-usable. So why learn about ad-hoc commands first? Ad-hoc commands demonstrate the simplicity and power of Ansible. The concepts you learn here will port over directly to the playbook language

### Why use ad-hoc commands?

Ad-hoc commands are great for tasks you repeat rarely. For example, if you want to power off all the machines in your lab for Christmas vacation, you could execute a quick one-liner in Ansible without writing a playbook. An ad-hoc command looks like this:

    $ ansible [pattern] -m [module] -a "[module options]"
    
### Setup Module

To get information about the network or hardware or OS version or memory related information the setup module will help to gather the same about the target machines. On the control, the machine runs the below command.

    $ anisble web -m setup 
    
