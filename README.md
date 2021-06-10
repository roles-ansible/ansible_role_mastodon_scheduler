 ansible role mastodon_scheduler
=================================

[![Galaxy](https://raw.githubusercontent.com/roles-ansible/ansible_role_mastodon_scheduler/main/.github/galaxy.svg)](https://galaxy.ansible.com/do1jlr/mastodon_scheduler)
[![License](https://raw.githubusercontent.com/roles-ansible/ansible_role_mastodon_scheduler/main/.github/license.svg)](https://github.com/roles-ansible/ansible_role_mastodon_scheduler/blob/main/LICENSE)

[![Galaxy release](https://github.com/roles-ansible/ansible_role_mastodon_scheduler/actions/workflows/galaxy.yml/badge.svg)](https://github.com/roles-ansible/ansible_role_mastodon_scheduler/actions/workflows/galaxy.yml)
[![Ansible Lint check](https://github.com/roles-ansible/ansible_role_mastodon_scheduler/actions/workflows/ansible-linting-check.yml/badge.svg)](https://github.com/roles-ansible/ansible_role_mastodon_scheduler/actions/workflows/ansible-linting-check.yml)
[![Yamllint GitHub Actions](https://github.com/roles-ansible/ansible_role_mastodon_scheduler/actions/workflows/yamllint.yaml/badge.svg)](https://github.com/roles-ansible/ansible_role_mastodon_scheduler/actions/workflows/yamllint.yaml)

Ansible role that can schedule Mastodon toots, created by a python3 script using [Mastodon.py](https://mastodonpy.readthedocs.io/en/stable/).

Here you are expected to have a pythonscript ready in a private git repository that can write Mastodon messages. This Ansible role generates an ssh key pair to clone the git repository, installs any python dependencies that are specified, and runs the script as many times as defined via systemd timer.

+ We create a user and a group, definied in the following variables:
```yaml
mastodon_scheduler__user: 'mastodon'
mastodon_scheduler__group: 'mastodon'
```

+ define the ssh clone url and branch, tag or commit hash in the following variables:
```yaml
mastodon_scheduler__private_repo: false
mastodon_scheduler__version: 'main'
```

+ Define the script name we should execute:
```yaml
mastodon_scheduler__exec: 'schedule.py'
```

+ Python Requirements we may need:
```yaml
mastodon_scheduler__pip_packages:
  - 'Mastodon.py'
```

+ Define the systemd Timer Execution time:
```yaml
# the default time is every Thursday at 23:42:23
mastodon_scheduler__time: 'Thu *-*-* 23:42:23'
```
