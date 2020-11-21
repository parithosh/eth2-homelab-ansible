# Ansible for Homelab

These ansible playbooks can be used to setup and maintain your homelab, aimed at ethereum related tasks.  

This repository contains an ansible playbook that can be used to perform the following:
- Setup a nethermind node

## Requirements: 
- A machine with ansible installed (https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- A remote server or VM running Ubuntu or Debian

## Setup:
- Clone this repository and navigate the terminal to the directory
- Open the `inventory.ini` file and enter the information as described
- Run the desired playbook with `ansible-playbook playbooks/<name-of-playbook-here>.yml`
- To confirm if its running fine, SSH into the machine check the playbook that was run

## Contributors welcome!
