Bind Role
=========

This role will configure the bind9 based on a template and variables.

[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-neoloc.bind-blue.svg)](https://galaxy.ansible.com/neoloc/ansible-role-bind/)


Requirements
------------

All requirements met by default ansible tooling.

Role Variables
--------------

Refer to the `defaults/main.yml` file for full details.

```yaml
# bind settings
bind_configure: True
bind_port: 53
bind_caching_dns: yes
bind_dnssec_validation: auto
bind_dnssec_validate_except:
  - dmz.domain.tld
  - prod.domain.tld
  - network.domain.tld
  - 8.10.10.in-addr-arpa

bind_zones:
  - name: dmz.domain.tld
    type: forward
    zone_forwarders:
      - 10.10.8.32
      - 10.10.8.33
  - name: network.domain.tld
    type: forward
    zone_forwarders:
      - 10.10.8.32
      - 10.10.8.33
  - name: 8.10.10.in-addr.arpa
    type: forward
    zone_forwarders:
      - 10.10.8.32
      - 10.10.8.33

bind_allow_recursion:
  - 10.10.8.0/24
  - 127.0.0.1

bind_options_listen_on:
  - any

bind_options_listen_on_v6:
  - any

bind_options_forwarders:
  - 8.8.8.8
  - 8.8.4.4
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - neoloc.bind

License
-------

See license.md

Author Information
------------------

[![Github](https://img.shields.io/badge/Github-neoloc-blue.svg)](https://github.com/neoloc)
