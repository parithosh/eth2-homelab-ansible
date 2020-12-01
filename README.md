# Ansible for Homelab and Eth2 tasks

These ansible playbooks can be used to setup and maintain your homelab. The playbooks will largely be aimed at eth2 
tasks.  

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

If you like my work, feel free to toss me some eth.

Ethereum address: 0x2628562A4fd5762D52CF43DE21bB925174C33085

