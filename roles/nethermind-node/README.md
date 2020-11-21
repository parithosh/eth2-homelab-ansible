# Ansible for nethermind

This role contains an code that can be used to perform the following:
- Setup a nethermind node


## Setup:
- Add this role in a playbook
- Run said playbook

## Caveats:
- This script currently just works to setup a nethermind node. It will not work on opernethereum or geth.
- The ansible script sets up nethermind as a SystemD service. Which is hard if you don't like systemd. 
- Metrics are enabled by default, please disable them if you wish
- The ansible script runs nethermind in fast sync mode, please edit the script to change the sync mode

## Future work:
- Monitoring setup could also be run alongside

## Contributors welcome!
