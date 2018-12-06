sudoers_apply
=============

Configure sudoers from a template. A rollback feature ensures you will not be
locked out of root privileges on the target host.

Requirements
------------

None.

Role Variables
--------------

This role can be set using the following variables:

* The filename of the sudoers configuration fragment to install in
  `/etc/sudoers.d`.

```yaml
sudoers_apply__filename: sudoers_apply
```

* Path of a template file that once evaluated is used as a sudoers
  configuration fragment.

```yaml
sudoers_apply__template: sudoers_apply.j2
```

* The delay, in seconds, after what the initial sudo configuration is
  reloaded if the confirmation file is missing.

```yaml
sudoers_apply__timeout: 20
```

Dependencies
------------

None.

Example Playbook
----------------

Apply new set of `Defaults` options from a specific template.

```yaml
- hosts: servers
  roles:
    - role: sudoers_apply
      sudoers_apply__filename: 00_defaults
      sudoers_apply__template: sudoers.d/00_defaults.j2
```

License
-------

GPLv3

Author Information
------------------

<quidame@poivron.org>
