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
You can simply install this role on your machine or hosts by using the below command:
```bash
ansible-galaxy install hamidyousefi.docker
```
Also, if you defined your playbook, you can simply add below lines to your `roles/requirements.yml`.
You can create this file if your playbook doesn't have it yet.
```yaml
- name: hamidyousefi.docker
  version: master
```
`master` is the most updated version of this role. You should 
define which version you are going to use just by replacing it with something like `v1.3.0`.
You can find the versions list and their changelogs from 
[releases page](https://github.com/hamidyousefi/ansible-docker/releases).

## Login to Registries
This role can login the defined users into specified registries. Below code shows how it is possible:
```yaml
docker_registries:
  - user: linux-user
    url: registry.domain.tld
    username: registry-username
    password: '123456'
```

## Additional Extensions and Configurations
I added few extra features to this role. `docker-compose` and or service level proxy can be set up easily just
by adding the below block in your `group_vars` or `host_vars` related YAML files.

### Docker Compose
Installing `docker-compose` will be installed by default. If you don't want to install it, add below block to
your variable:
```yaml
extensions: []
```
Additionally, You can add your `docker-compose.yml` files to the targeted remote host and paths.
Configure the below values in your group or host variables.
```yaml
docker_compose:
  - template_path: where-the-template-placed/docker-compose.yml.j2
    destination_path: path-to-place/docker-compose.yml
```

### HTTP(S) Proxy
If you want to configure http and (or) https proxy on your docker, you can add below
variables:
```yaml
docker_proxy:
  http: 'http://your-server:80'
  https: 'https://your-server:443'
```
