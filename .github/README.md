# ans_role_config_zfs_datasets

Create and configure zfs _filesystem-datasets_.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_config_zfs_datasets.svg?label=release)](https://github.com/digimokan/ans_role_config_zfs_datasets/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Role Options](#role-options)
* [Contributing](#contributing)

## Purpose

* Create zfs [_filesystem-datasets_](https://openzfs.github.io/openzfs-docs/man/8/zfs-create.8.html#DESCRIPTION).
* Configure loading of datasets at boot.

## Supported Operating Systems

* FreeBSD.

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_config_zfs_datasets
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Create and configure zfs filesystem datasets"
         ansible.builtin.include_role:
           name: ans_role_config_zfs_datasets
         vars:
           filesystem_datasets:
             - { pool: 'zroot', path: '/home',             mount: '/home',     owner: 'root',  group: 'wheel', mode: '755' }
             - { pool: 'zroot', path: '/home/user2',       mount: 'inherited', owner: 'user2', group: 'user2', mode: '710' }
             - { pool: 'zroot', path: '/home/user2/Trash', mount: 'inherited', owner: 'user2', group: 'user2', mode: '755' }
   ```

## Role Options

Vars with default values, which can be overridden in the playbook:

  * [overridable](../defaults/main/overridable)

Vars defined by this role, exported with `public: true`, for use in other roles:

  * [export](../defaults/main/export/commands.yml)

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_config_zfs_datasets/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).

