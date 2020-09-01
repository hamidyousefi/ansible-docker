# Docker Installation Ansible Role

This is a very simplified Ansible role for installing Docker as a systemd service.

## Supporting Distributions and Their Releases
- Debian
    - Stretch
    - Buster
- Ubuntu
    - Xenial
    - Bionic
    - Focal
    
## Installation
Everywhere in your controller machine, you just need to install it via
```bash
ansible-galaxy install hamidyousefi.docker
```
Then you can use this role in your Ansible Playbooks like:
```yaml
---
- hosts: baremetals
  roles:
    - hamidyousefi.docker
```
