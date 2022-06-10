# coastsat-public-keys
This repo is used to place public keys onto the coastal mapping virtual machines

## How to add a key

Create a new branch and add your contents of your public key to the authorized.crt file. 

You should then create a new pull request from your branch, this should be reviewed and approved by Heike, Erin, or Noelle

The key will be pulld once merged into the main after the cronjob runs on the virutal machines. The current configured time is running the git pull every 10 mins.

## How it is configured

``*/10 * * * * su -s /bin/sh acep -c 'cd ~/.nx/config && /usr/local/bin/git pull -q origin main'``

The acep user has a .nx folder that the repo is mapped to the config folder. the player config settings are not saved but the authorized.crt file is tracked in this repo.

The repo must be public so that the system can pull updates. There is no sensitive secrets in this file.


### Potential future upgrades

This project could use SSH deploy keys and make this repo private. 
