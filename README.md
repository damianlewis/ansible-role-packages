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
- `install_recommended_packages:boolean` - Defaults to `packages_install_recommended_packages` if omitted (see below).
  - `true` - Any recommended packages associated with the named package will also be installed. 
  - `false` - Recommended packages aren't installed. 

```yaml
packages_to_remove: []
```
A list of packages to remove.

The following attributes are required:
- `name:string` - Name of the package to remove.

The following attributes are optional:
- `purge:boolean` - Defaults to `packages_purge` if omitted (see below).
  - `true` - The configuration files associated with the package will also be removed. 
  - `false` - Configuration files are left in place. 
 
```yaml
packages_update_cache: no
packages_cache_valid_time: 3600
```
- `packages_update_cache:boolean`
  - `true` - The packages cache (the package index files) will be updated.
  - `false` - The packages cache isn't updated.
- `packages_cache_valid_time:integer` - The number of seconds to keep the current packages cache before updating it. If the packages cache was updated more then `packages_cache_valid_time` seconds ago, then it will be updated.

```yaml
packages_clean_system: no
```
- `packages_clean_system:boolean`
  - `true` - Any redundant packages will be removed using the apt 'autoclean' and 'autoremove' commands.
  - `false` - Redundant packages aren't removed.

```yaml
packages_install_recommended_packages: no
packages_purge: no
```
Default settings.
- `packages_install_recommended_packages:boolean` - The default behaviour for installing recommended packages.
- `packages_purge:boolean` - The default behaviour for purging packages.

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