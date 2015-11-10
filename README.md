Ansible Role: brew
==================

[![Build Status](http://img.shields.io/travis/jgkim/ansible-role-brew.svg?style=flat)](https://travis-ci.org/jgkim/ansible-role-brew)
[![Ansible Galaxy](http://img.shields.io/ansible/role/5869.svg?style=flat)](https://galaxy.ansible.com/detail#/role/5869)

This role ensures that Homebrew and its configured packages are installed on OS X.


Requirements
------------

* Xcode Command Line Tools


Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

```
brew_dir: /opt/homebrew
```

The path where Homebrew will be installed. By default, it will install Homebrew to `/opt/homebrew`. Some things may not build when installed here, but to avoid [security issues](https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/El_Capitan_and_Homebrew.md) and `/usr/local` being a mess with other stuff, it is recommend stick to this default.

```
brew_taps: []
```

Taps you would like to make sure Homebrew has added via `brew tap`.

```
brew_upgrade_all: False
```

Whether to update Homebrew and upgrade all packages installed by it. If you prefer to manually update packages via `brew` command, leave this set to `False`.

```
brew_packages: []
```

Packages you would like to make sure are installed via `brew install`.

```
app_dir: /Applications
```

The path where applications will be installed. By default, it will install applications to `/Applications`.

```
cask_packages: []
```

Packages you would like to make sure are installed via `brew cask install`.


Dependencies
------------

None.


Example Playbook
----------------

```
- hosts: localhost
  connection: local
  vars:
    brew_taps:
      - homebrew/completions
    brew_upgrade_all: True
    brew_packages:
      - wget
    cask_packages:
      - google-chrome
  roles:
     - { role: jgkim.brew }
```


License
-------

MIT


Author Information
------------------

This role was written by [James G. Kim](http://jayg.org/), after being inspired by others.
