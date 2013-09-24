playbook-server-deploy
======================

An Ansible playbook for new server deployment. Useful for setting up newly provisioned VPS.

## What it does
* Upate all packages
* Install "essential" tools
* Create wheel group, add your user, add user to wheel group, lock password, add ssh authorized key for user
* Install sudo, copy over sudoers for passwordless sudo for user, validate sudoers
* Install sshd_config that disables password login

## Requirements
* Ansible installed on client
* root username/password on server, ssh installed

## Vars and setup
You will need to copy `group_vars/all.example` to `group_vars/all` then edit `group_vars/all` with the user you wish to create on the server.

Also copy `hosts.example` to `hosts` and enter the ip or hostname of your server in place of the ip.

By default we try to login with root via ssh, if you have another user with sudo access on your server(e.g. Amazon) edit `site.yml` and change the user and uncomment the sudo line. 

## Running the play
`ansible-playbook -k -i hosts site.yml`
