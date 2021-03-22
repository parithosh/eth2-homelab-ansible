# Ansible for Homelab and Eth2 tasks

These ansible playbooks can be used to setup and maintain your homelab. The playbooks will largely be aimed at eth2 
tasks. The nethermind node also has flags enabled to minimize size, yet provide all the functionality for the eth2 
mainnet. 

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

## Note: 
- In case you want to run Nethermind for goerli instead of mainnet, open the `roles/nethermind-node/files/nethermind.service`
file and add edit the `ExecStart` command: `ExecStart=/chaindata/nethermind/Nethermind.Runner  --config goerli --Network.MaxActivePeers 25 --JsonRpc.Enabled true --JsonRpc.Host 0.0.0.0`
- I prefer running Nethermind as a systemD service since I have found it to be more stable, your mileage may vary. 

## Contributors welcome!

If you like my work, feel free to toss me some eth.

Ethereum address: 0x2628562A4fd5762D52CF43DE21bB925174C33085
