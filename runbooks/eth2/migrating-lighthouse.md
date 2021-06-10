# Migration guide for Lighthouse Validator

Note: Important: Ensure that you are working with the right data directory, Lighthouse by default goes to
`$HOME/.lighthouse`. Also ensure permissions are set correctly.

1. Ensure that there is a synced eth1 node, synced beacon node (ideally also lighthouse @ same version)
2. Stop the lighthouse validator with `sudo service lighthousevalidator stop`
3. Check logs to ensure its stopped
4. Wait 1 epoch to ensure a vote is missed and the validator is indeed offline
5. On the old machine, run `./lighthouse account validator slashing-protection export interchange.json`, this will transfer
the info in the `slashing_protection.sqlite` db into a `json` file. If the slashing protection DB is in a non-standard location
   then add the flag `--datadir <path>`
6. Check the contents on the `json` to ensure its filled with data. `cat interchange.json`
7. Move the `validator_keystore` and `interchange.json` into the new machine. `scp -r old_path/validator_keystore new-machine:path`
8. Ensure the latest version of lighthouse (or same as beacon) is present on the new machine
9. Copy over the `lighthousevalidator.service` unit file from the old machine to the new, ensure lighthouse is in the correct
location and that the lighthouse user is present
10. Import the keys with `./lighthouse --network mainnet account validator import --directory validator_keys --datadir <path>`
11. Import the slashing DB with `./lighthouse account validator slashing-protection import interchange.json --datadir <path>`
12. Ensure that you have waited atleast 3 epochs to prevent slashing
13. Ensure that the lighthouse dir has the right permission, the user `lighthouse` should have `rw` permissions    
14. Reload the systemctl daemon with `sudo systemctl daemon-reload`
15. Start lighthouse validator with `sudo service lighthousevalidator start`
16. Check the logs with `sudo journalctl -fu lighthousevalidator`
17. Monitor attestations on `beaconchain` for a few epochs