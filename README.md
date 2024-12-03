[![build-test](https://github.com/darkwizard242/ansible-role-eksctl/workflows/build-and-test/badge.svg?branch=master)](https://github.com/darkwizard242/ansible-role-eksctl/actions?query=workflow%3Abuild-and-test) [![release](https://github.com/darkwizard242/ansible-role-eksctl/workflows/release/badge.svg)](https://github.com/darkwizard242/ansible-role-eksctl/actions?query=workflow%3Arelease) ![Ansible Role](https://img.shields.io/ansible/role/d/darkwizard242/eksctl) [![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-eksctl&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=ansible-role-eksctl) [![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-eksctl&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=ansible-role-eksctl) [![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-eksctl&metric=security_rating)](https://sonarcloud.io/dashboard?id=ansible-role-eksctl) ![GitHub tag (latest SemVer)](https://img.shields.io/github/tag/darkwizard242/ansible-role-eksctl?label=release) ![GitHub repo size](https://img.shields.io/github/repo-size/darkwizard242/ansible-role-eksctl?color=orange&style=flat-square)

# Ansible Role: eksctl

Role to install (_by default_) [eksctl](https://github.com/weaveworks/eksctl) on **Debian/Ubuntu** and **EL** systems. **eksctl** is the offical CLI for Amazon EKS.

## Requirements

None.

## Role Variables

Available variables are listed below (located in `defaults/main.yml`):

### Variables list:

```yaml
eksctl_app: eksctl
eksctl_version: 0.197.0
eksctl_os: "{{ ansible_system }}"
eksctl_architecture_map:
  amd64: amd64
  arm: arm64
  x86_64: amd64
  armv6l: armv6
  armv7l: armv7
  aarch64: arm64
  32-bit: "386"
  64-bit: amd64
eksctl_dl_url: https://github.com/weaveworks/{{ eksctl_app }}/releases/download/v{{ eksctl_version }}/{{ eksctl_app }}_{{ eksctl_os }}_{{ eksctl_architecture_map[ansible_architecture] }}.tar.gz
eksctl_bin_path: /usr/local/bin
eksctl_file_owner: root
eksctl_file_group: root
eksctl_file_permission_mode: '0755'
```

### Variables table:

Variable                    | Description
--------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------
eksctl_app                  | Defines the app to install i.e. **eksctl**
eksctl_version              | Defined to dynamically fetch the desired version to install. Defaults to: **0.197.0**
eksctl_os                   | Defines os type.
eksctl_architecture_map     | Defines os architecture.
eksctl_dl_url               | Defines URL to download the eksctl binary from.
eksctl_bin_path             | Defined to dynamically set the appropriate path to store eksctl binary into. Defaults to (as generally available on any user's PATH): **/usr/local/bin**
eksctl_file_owner           | Owner for the binary file of eksctl.
eksctl_file_group           | Group for the binary file of eksctl.
eksctl_file_permission_mode | Defines the permission mode level for the file. Defaults to: `0755`

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
