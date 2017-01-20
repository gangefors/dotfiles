
Prerequisites
-------------

- Git

        sudo apt-get install git

- Ansible

  http://docs.ansible.com/ansible/intro_installation.html


Configure new machines
----------------------

To deploy everything to a new machine run:

    ansible-playbook deploy-all.yml --ask-become-pass

To only run parts of the deployment separate playbooks is available.

- `system-plays.yml`

    This playbook contains all plays that in some way needs `sudo` privileges.

- `user-plays.yml`

    This playbook contains all plays that only affect the users environment.

Tags are also available to run specific parts.

- install

    This tag runs all tasks that install packages or any type of software.

- configure

    This tag runs only tags that do configuring of the system. Typically
    updates of .rc or .conf files, etc.
