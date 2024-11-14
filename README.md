# Ansible Role: devbox-role

## Overview

This Ansible role sets up a development environment on Red Hat Enterprise Linux 9 (RHEL 9) or compatible systems. It installs and configures the following tools:

- Go (Golang)
- Node.js
- Hugo

The role is designed to quickly set up a consistent development environment across multiple machines.

## Requirements

- Ansible 2.14 or higher
- RHEL 9 or compatible target systems (e.g., CentOS Stream 9, Rocky Linux 9)
- Podman (for running tests with Molecule)

## Role Behavior
This role performs the following actions:

1. Upgrades all packages on the target system
2. Installs Go using the gantsign.golang role
3. Installs Node.js using the andrewrothstein.node role
4. Installs Hugo using the andrewrothstein.hugo role

## Role Variables

This role currently does not define any variables in `defaults/main.yml` It uses the default configurations provided by the dependent roles. You can override these by setting variables in your playbook or inventory.

## Dependencies

This role depends on the following Ansible Galaxy roles:

- `andrewrothstein.node`: For installing Node.js
- `gantsign.golang`: For installing Go
- `andrewrothstein.hugo`: For installing Hugo

These dependencies are automatically installed when you use the `requirements.yml` file.

## Installation

To use this role in your Ansible projects:

1. Add the following to your `requirements.yml` file:

```yaml
   - src: https://github.com/apigban/devbox-role.git
     name: apigban.devbox-role'
```

2. Run `ansible-galaxy install -r requirements.yml`


## Example Playbook
```
- hosts: dev_servers
  roles:
     - apigban.devbox-role
```