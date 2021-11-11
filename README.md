[![build-test](https://github.com/darkwizard242/ansible-role-eksctl/workflows/build-and-test/badge.svg?branch=master)](https://github.com/darkwizard242/ansible-role-eksctl/actions?query=workflow%3Abuild-and-test) [![release](https://github.com/darkwizard242/ansible-role-eksctl/workflows/release/badge.svg)](https://github.com/darkwizard242/ansible-role-eksctl/actions?query=workflow%3Arelease) ![Ansible Role](https://img.shields.io/ansible/role/47495?color=dark%20green%20) ![Ansible Role](https://img.shields.io/ansible/role/d/47495?label=role%20downloads) ![Ansible Quality Score](https://img.shields.io/ansible/quality/47495?label=ansible%20quality%20score) [![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-eksctl&metric=alert_status)](https://sonarcloud.io/dashboard?id=ansible-role-eksctl) [![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-eksctl&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=ansible-role-eksctl) [![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-eksctl&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=ansible-role-eksctl) [![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-eksctl&metric=security_rating)](https://sonarcloud.io/dashboard?id=ansible-role-eksctl) ![GitHub tag (latest SemVer)](https://img.shields.io/github/tag/darkwizard242/ansible-role-eksctl?label=release) ![GitHub repo size](https://img.shields.io/github/repo-size/darkwizard242/ansible-role-eksctl?color=orange&style=flat-square)

# Ansible Role: Hugo

Role to install (_by default_) [eksctl](https://github.com/weaveworks/eksctl) on **Debian/Ubuntu** and **EL** systems. **eksctl** is the offical CLI for Amazon EKS.

## Requirements

None.

## Role Variables

Available variables are listed below (located in `defaults/main.yml`):

### Variables list:

```yaml
eksctl_app: eksctl
eksctl_version: 0.73.0
eksctl_osarch: amd64
eksctl_dl_url: https://github.com/weaveworks/{{ eksctl_app }}/releases/download/v{{ eksctl_version }}/{{ eksctl_app }}_Linux_{{ eksctl_osarch }}.tar.gz
eksctl_bin_path: /usr/local/bin
```

### Variables table:

Variable        | Description
--------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------
eksctl_app      | Defines the app to install i.e. **eksctl**
eksctl_version  | Defined to dynamically fetch the desired version to install. Defaults to: **0.73.0**
eksctl_osarch   | Defines os architecture. Used for obtaining the correct type of binaries based on OS System Architecture.
eksctl_dl_url   | Defines URL to download the eksctl binary from.
eksctl_bin_path | Defined to dynamically set the appropriate path to store eksctl binary into. Defaults to (as generally available on any user's PATH): **/usr/local/bin**

## Dependencies

None

## Example Playbook

For default behaviour of role (i.e. installation of **eksctl**) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.eksctl
```

For customizing behavior of role (i.e. specifying the desired **eksctl** version) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.eksctl
  vars:
    eksctl_version: 0.72.0
```

For customizing behavior of role (i.e. placing binary of **eksctl** package in different location) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.eksctl
  vars:
    eksctl_bin_path: /bin/
```

## License

[MIT](https://github.com/darkwizard242/ansible-role-eksctl/blob/master/LICENSE)

## Author Information

This role was created by [Ali Muhammad](https://www.alimuhammad.dev/).