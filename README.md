Role Name: ajeleznov.manage-known-hosts
=========

This role makes it possible to make a ssh connection to remote servers without being asked:
```
The authenticity of host 'XXX (XX.XX.XX.XX)' can't be established
...
Are you sure you want to continue connecting (yes/no)?
```
It enables this by saving the host public keys in the system-wide known_hosts file.
You assign the name of a server or a group of servers from inventory to hosts variable,
for which you want to enable this functionality.
And you list the servers that should be known in the variable known_hosts_target_group.
I use short names for server name that why you need to supply a domain name in the net_domain variable.

Role Variables
--------------

See defaults/main.yml

Example Playbook
----------------
```
hosts:		                              test
gather_facts:                           True

tasks:
	- import_role:
	    name:                             ajeleznov.manage-known-hosts
    vars:
      known_hosts_target_group:
                - serverA
                - serverB
      net_domain:                       ".example.com"
      enable_global_known_host_keys:    True
      replace_global_known_hosts_file:  False
```

License
-------

MIT


Author Information
------------------

Dr. Andrei Jeleznov <mailto:andrei.jeleznov@kuehne-nagel.com>

