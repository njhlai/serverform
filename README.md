# ServerForm

## About
A server configuration, deployment and management automation via infrastructure-as-code, using [Ansible](https://www.ansible.com). ServerForm configures and manages servers using rules defined by a collection of Ansible playbooks and roles.

## Requirements
- [Python](https://www.python.org): 3.8
- [Ansible](https://www.ansible.com): 2.4

## Usage
Supply ServerForm with an Ansible-acceptable inventory file (see [Ansible's documentation for inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)) which details your server setup and specify the path via the `INVENTORY` argument in `ansible.cfg`. 

## Roles 
Here are the roles which have been implemented:
- [Pi-hole](https://pi-hole.net): A DNS adblocker on ARM-based boards.
- [log2ram](https://github.com/azlux/log2ram): A ramlog for systemd, to prevent log-writing to SD cards.
- [mergerfs](https://github.com/trapexit/mergerfs): A union filesystem that pools access across multiple drives.