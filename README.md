Prerequisites
-------------

### On the local host

- Ansible
- Git
- Python

### On the remote host

- Python
- SSH Server


Configure new machines
----------------------

To deploy everything to a new machine run:

    ansible-playbook deploy-all.yml -i inventory

To limit deployment to only one host or group of hosts.

    ansible-playbook deploy-all.yml -i inventory -l <host/group>

Check the `inventory` file for a list of groups and hosts or add more.

### Partial deployment
The deployment has been devided into two major plays.

- `system`

    This play consists of tasks that in some way needs `sudo` privileges.
    _Use --ask-become-pass when running those plays if you haven't configured
    passwordless sudo._

- `user`

    This play contains all tasks that only affect the user environment.

To only run the `user` part of the deployment do this:

    ansible-playbook user-plays.yml -i inventory

These plays are further divided into smaller groups denoted by tags.

- `install`

    This tag is on all tasks that download and install packages.

- `configure`

    This tag runs only tasks that do configuration of the system. Typically
    updates of .rc or .conf files, symlinking of dotfiles, etc.

To run only configuring tasks for the user this will do the trick:

    ansible-playbook user-plays.yml -i inventory -t configure
