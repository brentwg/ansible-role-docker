# Ansible Role: Docker CE
[![Build Status](https://travis-ci.org/brentwg/ansible-role-docker.svg?branch=master)](https://travis-ci.org/brentwg/ansible-role-docker)  

Ansible role that installs Docker CE.

## Requirements  

None.  

## Role Variables  

User modifiable variables and defaults are listed below. (For all variables, see `defaults/main.yml`):  
```
docker_package_name: docker-ce
docker_package_state: present
docker_gpg_key_url: https://download.docker.com/linux/centos/gpg
```  
Not bothering with 'Enterprise Edition' here. You can control whether to install/remove/update Docker using by setting `docker_package_state` to `present`, `absent`, or `latest` respectively.  
```
# Docker Compose options.
docker_install_compose: true
docker_compose_version: "1.19.0"
docker_compose_path: /usr/local/bin/docker-compose
```  
Docker Compose installation options.  
```
# Used only for Debian/Ubuntu
docker_apt_release_channel: stable
docker_apt_repository: "deb https://download.docker.com/linux/{{ ansible_distribution|lower }} {{ ansible_distribution_release }} {{ docker_apt_release_channel }}"
```  
Used only for Debian/Ubuntu.

In addition, there are distribution specific variables for `Redhat` family distributions set in the `vars` directory.  

```
---
docker_packages_old:
  - docker
  - docker-client
  - docker-client-latest
  - docker-common
  - docker-latest
  - docker-latest-logrotate
  - docker-logrotate
  - docker-engine

docker_yum_repo_url: https://download.docker.com/linux/centos/docker-ce.repo
```
For `CentOS 7`.  

```
docker_packages_old:
  - - docker
    - docker-client
    - docker-common
    - docker-latest
    - docker-latest-logrotate
    - docker-logrotate
    - docker-selinux
    - docker-engine-selinux
    - docker-engine
    
docker_yum_repo_url: https://download.docker.com/linux/fedora/docker-ce.repo

```  
For `Fedora 27`.  

## Dependencies

None.  

## Sample Playbook
```
- hosts: all
  
  roles:
    - brentwg.docker
```
