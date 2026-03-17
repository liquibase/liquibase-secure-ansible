# Liquibase Secure Ansible Role

![Build Status](https://github.com/liquibase/liquibase/actions/workflows/build.yml/badge.svg)

The Liquibase Secure Ansible role installs [Liquibase Secure](http://www.liquibase.org).

## Requirements

See [meta/requirements.yml](meta/requirements.yml)

## Role Variables

* **liquibase_ver**: The version of Liquibase Secure to install. **Default value** -> `5.1.0`
* **liquibase_mirror**: The mirror from which Liquibase Secure releases are downloaded. **Default value** -> `https://package.liquibase.com/downloads/secure/ansible`
* **liquibase_parent_install_dir**: The parent installation directory for Liquibase Secure. **Default value** -> `/usr/local`
* **liquibase_checksums**: SHA-256 checksums for each Liquibase Secure release, used to verify the integrity of downloaded files.

## Example Playbook (installs latest liquibase-secure release)

```yml
- hosts: server
  roles:
    - role: liquibase.liquibase-secure
```

## Example Playbook (installs liquibase-secure 5.1.0)

```yml
- hosts: server
  roles:
    - role: liquibase.liquibase-secure
      liquibase_ver:
        - 5.1.0
```

## Example Playbook installation process

Let's say you would like to have `liquibase-secure` installed in 3 AWS ec2 instances.

* **Set up your inventory**: Create an inventory file (`inventory.ini`) listing the IP addresses or hostnames of your three EC2 instances.

```bash
[liquibase_hosts]
10.0.0.1
10.0.0.2
10.0.0.3
```

* **Install the Liquibase Secure Ansible role**: The Liquibase Secure Ansible role is available on Ansible Galaxy, you can install it using the ansible-galaxy command:

```bash
ansible-galaxy role install liquibase.liquibase-secure
```

* **Write your playbook**: Create an Ansible playbook (`playbook.yml`) that uses the Liquibase Secure role and targets the hosts specified in your inventory file:

```yml
- name: Install Liquibase Secure
  hosts: liquibase_hosts
  become: yes
  roles:
    - liquibase.liquibase-secure
```

* **Run your playbook**: Execute the playbook against your inventory using the `ansible-playbook` command:

```bash
ansible-playbook -i inventory.ini playbook.yml
```

This command will install Liquibase Secure on the specified EC2 instances.

* **Verify**: After running the playbook, verify that Liquibase Secure was installed successfully on all three EC2 instances. You may need to log in to each instance and check the installation.

## Standalone role install

### Install the role

```bash
ansible-galaxy role install liquibase.liquibase-secure
```

### Uninstall the role

```bash
ansible-galaxy role remove liquibase.liquibase-secure
```

### Upgrade the role

The recommended path to update a role is to use the `--force` option

```bash
ansible-galaxy install --force liquibase.liquibase-secure
```
