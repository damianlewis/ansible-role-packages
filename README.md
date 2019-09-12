# Ansible Role: Packages
Ubuntu/Debian package management role.

## Requirements
None.

## Role Variables
Available variables are listed below, along with their default values.

```yaml
packages_to_add: []
```
A list of packages to install.

The following attributes are required:
- `name:string` - Name of the package to install.

The following attributes are optional:
- `install_recommended_packages:boolean` - If set to true, any recommended packages associated with the named package will also be installed. Defaults to false if omitted (see `packages_default_install_recommended_packages` below).

```yaml
packages_to_remove: []
```
A list of packages to remove.

The following attributes are required:
- `name:string` - Name of the package to remove.

The following attributes are optional:
- `purge:boolean` - If set to true, the configuration files associated with the package will also be removed. Defaults to false if omitted (see `packages_default_purge` below).

```yaml
packages_update_cache: no
packages_cache_valid_time: 3600
```
- `packages_update_cache:boolean` - If set to true, the packages cache (the package index files) will be updated using thier source.
- `packages_cache_valid_time:integer` - The number of seconds to keep the current packages cache before updating it. If the packages cache was updated more then `packages_cache_valid_time` seconds ago, then it will be updated.

```yaml
packages_clean_system: no
```
- `packages_clean_system:boolean` - If set to true, any redundant packages will be removed using the apt 'autoclean' and 'autoremove' commands.

```yaml
packages_default_install_recommended_packages: no
packages_default_purge: no
```
Default settings.
- `packages_default_install_recommended_packages:boolean` - The default behaviour for installing recommended packages.
- `packages_default_purge:boolean` - The default behaviour for purging packages.

## Dependencies
None.

## Example Playbook
```yaml
- hosts: server
  become: yes

  vars:
    packages_to_add:
    - name: apache2
    - name: apache2-utils

  tasks:
  - import_role:
      name: damianlewis.packages
```

## License
MIT

## Author
Damian Lewis