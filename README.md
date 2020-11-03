# Docker Ansible Role
This is a very simplified Ansible Role for installing Docker as a systemd service.
I'm using this role for many personal and enterprise projects and will do my best to keep it
update and customizable with the latest changes which would be useful for me (and others).

## Distributions and Their Releases
Right now, these OS distributions and releases are tested:
- Debian
    - Jessie
    - Stretch
    - Buster
- Ubuntu
    - Xenial
    - Bionic
    - Focal
    
## How to Use It
You can simply install this role on your machine by using the below command:
```bash
ansible-galaxy install hamidyousefi.docker
```
Also if you defined your playbook, you can simply add below lines to your `roles/requirements.yml`.
You can create this file if your playbook doesn't have it yet.
```yaml
- name: hamidyousefi.docker
  version: master
```
Of course `master` is the most updated version of this role. You should prefer to 
define which version you are going to use just by replacing it with something like `v1.0.0`.
You can find the versions list and their changelogs from [releases page](https://github.com/hamidyousefi/ansible-docker/releases).

## Additional Extensions and Configurations
I added three specific extra feature to this role. `docker-compose` and `iptables` can be set up easily just
by adding the below block in your `group_vars` related YAML file:
```yaml
configure:
  compose: yes
  iptables: yes
  proxy: no
```

## HTTP(S) Proxies
If you have to configure http and (or) https proxy on your docker, you can change
the ```proxy``` parameter in above section from ```no``` to ```yes```, and add below
variables into necessary host or group variables.
```yaml
docker_proxy:
  http: 'http://your-server:80'
  https: 'https://your-server:443'
```
