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
- [bmajor](https://github.com/njhlai/serverform/tree/master/roles/bmajor): Configures bmajor hosts for bminor servers, which pulls backups from bminor servers via [rsnapshot](https://rsnapshot.org).
- [bminor](https://github.com/njhlai/serverform/tree/master/roles/bminor): Specifies backup strategy to bmajor hosts via [rsync](https://rsync.samba.org).
- [diskconf](https://github.com/njhlai/serverform/tree/master/roles/diskconf): Configures disk by partitioning and formatting, and installs [Keith Nash's disk burn-in script](https://github.com/Spearfoot/disk-burnin-and-testing) and a SMART reporting script [which is based on this](https://www.truenas.com/community/threads/scripts-to-report-smart-zpool-and-ups-status-hdd-cpu-t%C2%B0-hdd-identification-and-backup-the-config.27365/).
- [log2ram](https://github.com/njhlai/serverform/tree/master/roles/log2ram): Configures [log2ram](https://github.com/azlux/log2ram), a ramlog for systemd, to prevent log-writing to SD cards.
- [mergerfs](https://github.com/njhlai/serverform/tree/master/roles/mergerfs): Configures [mergerfs](https://github.com/trapexit/mergerfs), a union filesystem that pools access across multiple drives.
- [pihole](https://github.com/njhlai/serverform/tree/master/roles/pihole): Configures [Pi-hole](https://pi-hole.net), a DNS adblocker on ARM-based boards.
- [samba](https://github.com/njhlai/serverform/tree/master/roles/samba): Configure [Samba](https://www.samba.org), a network file sharing using SMB protocol.

## Inspirations
Here are some of wonderful implementations of which I based a lot of my roles on.
- [Alex Kretzschmar's Github for his Ansible roles](https://github.com/IronicBadger/ansible) is a wonderful place to start, and I especially based a lot of my mergerfs role on his. Incidentally, his [Perfect Media Server series of articles](https://blog.linuxserver.io/2019/07/16/perfect-media-server-2019/) is what inspired me to learn Ansible.
- I learnt Ansible from following Jeff Geerling's wonderful [YouTube series on Ansible](https://www.youtube.com/playlist?list=PL2_OBreMn7FplshFCWYlaN2uS8et9RjNG)
- The backup major-minor strategy (i.e. bmajor and bminor roles) using rsnapshot is heavily inspired from [Osiell's backup implementation](https://github.com/osiell/ansible-rsnapshot-master). Also consulted [Yannik's implementation](https://github.com/Yannik/ansible-role-rsnapshot-backup-host), and may implement some fancy backup scripts therein down the road.
- [Larry Smith Jr.'s Samba Ansible setup](https://github.com/mrlesmithjr/ansible-samba) provides the base for the samba role, especially the config file setup.