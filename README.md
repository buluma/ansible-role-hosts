# [Ansible role hosts](#hosts)

Ansible role that dynamically creates the hosts file.

|GitHub|Version|Issues|Pull Requests|
|------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-hosts/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-hosts/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-hosts.svg)](https://github.com/buluma/ansible-role-hosts/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-hosts.svg)](https://github.com/buluma/ansible-role-hosts/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-hosts.svg)](https://github.com/buluma/ansible-role-hosts/pulls/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-hosts/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.hosts
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-hosts/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.bootstrap
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-hosts/blob/master/defaults/main.yml):

```yaml
---
# defaults file for buluma.hosts

# Path to the host file on the target system.
hosts_file: /etc/hosts

# Backup the hosts file before changing it.
hosts_backup: false

# Group owner of hosts file.
hosts_group: root

# Owner of hosts file.
hosts_owner: root

# Settings for SElinux.
hosts_serole: object_r
hosts_setype: net_conf_t
hosts_seuser: system_u
hosts_selevel: s0

# Access permission hosts file.
hosts_mode: 0644

# Creates a 172.0.0.1 entry for the server name.
hosts_hostname_loopback: true

# Inserts all hosts in the Ansible Inventory
# file into the Hosts file
hosts_inventory_to_hosts: false

# If this option and the hosts_inventory_to_hosts is enabled it writes all private ip addresses from the inventory into the hosts
hosts_all_private: true

# If this option and the hosts_inventory_to_hosts is enabled it writes all public ip addresses from the inventory into the hosts.
hosts_all_public: false

# Ipv6 localhost entries are set automatically.
# Setting false it can be prevented.
hosts_ipv6: true

# Set ipv4 address (could be override by what you want)
hosts_ipv4_address: "{{ hostvars[inventory_hostname]['ansible_default_ipv4']['address'] }}"

# List of network cards that should not be added to the hosts file.
hosts_exludes_interfaces:
  - 'vet*'
  - 'docker'
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-hosts/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-hosts/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Alpine](https://hub.docker.com/repository/docker/buluma/alpine/general)|all|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|all|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|

The minimum version of Ansible required is 2.1, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-hosts/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-hosts/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-hosts/blob/master/LICENSE).

## [Author Information](#author-information)

[Michael Buluma](https://buluma.github.io/)


### [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
