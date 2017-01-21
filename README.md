
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

    ansible-playbook deploy-all.yml --ask-become-pass

To only run parts of the deployment separate playbooks is available.

- `system-plays.yml`

    This playbook contains all plays that in some way needs `sudo` privileges.
    _Use --ask-become-pass when running this play._

- `user-plays.yml`

    This playbook contains all plays that only affect the user environment.

Tags are also available to run specific parts.

- `install`

    This tag runs all tasks that install packages or any type of software.

- `configure`

    This tag runs only tags that do configuring of the system. Typically
    updates of .rc or .conf files, symlinking of dotfiles, etc.
