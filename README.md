# Readme for Xenserver vm deploys

This repo contains Ansible plays that can do automated installation of
Ubuntu on Xenserver.

## Automated installs on Xenserver

This section contains info about automated installations on Xenserver,
using Ansible.

#### Installation method

This automation expects an Ubuntu ISO to be present in xen
storage repository.

Planning to support network mode installation.

#### Preseed config

Preseeding provides a way to set answers to questions asked during the
installation process, without having to manually enter the answers
while the installation is running. This makes it possible to fully
automate most types of installation and even offers some features
not available during normal installations.

Preseed configuration can be used in different ways, here it's expected
to host the configuration file on a server.

This repo consists a sample configuration file, with description on
what each configuration does. Modify it as per your need and host it
on a server.

### Supported distros

- Ubuntu Precise 12.04

### IP assigning

This playbook allows user to configure static and dynamic IP.

#### Configure static IP

To configure static IP, set `disable_dhcp` as `true` and configure
following variables.
- `ipaddress`
- `gateway`
- `dnsservers`
- `netmaks`

### Usage

The following variables are required:

- `hostname`
- `domainname`
- `vm_name`
- `sr_name`
- `vm_template`
- `memory`
- `disksize`
- `cpu_weight`
- `vcpu_count`
- `os_iso`
- `preseed_url`

The hosts file contains a list of Xenservers. When running the script,
you have to limit the hosts it's being run on, to the one you wish the
VPS to run on. If you have a Xenserver pool, please use the poolmaster.

#### Example

`ansible-playbook -i hosts --limit xen01 xenserver-vm-deploy.yml -e
"hostname=vm01 vm_name=vm01 domainname=example.com"`
