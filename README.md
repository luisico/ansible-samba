Samba
======
Install [Samba](https://www.samba.org/samba/what_is_samba.html) server.

This roles supports server and client roles. For clients (default), `samba-client` is installed along with some dependencies, but do not prepare mounts or set up any configuration. For servers, the configuration is done via a `smb.conf` template managed by a few variables (see `defaults/main.yml` for details). You can configure any global option in dict `samba_global`, except the workgroup, which is configured in `samba_workgroup`. Any number of shares can be configure in dict `samba_shares`. Directories for defined samba shares will be created.

When using Samba's `user` security model (default), users in `samba_users` will be setup in the samba context, but note you still need to define them at the OS context (ie `/etc/passwd`, LDAP, ...).

Note that at least ports 139/tcp and 445/tcp need to be open for servers and clients.

Requirements
------------
See `meta/main.yml`.

Role Variables
--------------
See `defaults/main.yml` for all options.

Dependencies
------------
- Users need to be available to the OS when using Samba's `user` security  model.
- Firewall need to be open for ports 139/tcp and 445/tcp.

Example Playbook
----------------
Example:
```
- hosts: server
  roles:
    - {role: samba, samba_role: server}
```

TODO
----
- Configure samba client.
- Mount samba clients.

Licence
-------
Released under the [MIT license](https://opensource.org/licenses/MIT).

Author Information
------------------
Luis Gracia while at [The Rockefeller University](https://www.rockefeller.edu):
- lgracia [at] rockefeller.edu
- GitHub at [luisico](https://github.com/luisico)
- Galaxy at [luisico](https://galaxy.ansible.com/luisico)
