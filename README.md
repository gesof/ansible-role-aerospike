# Ansible Role: Aerospike

[![Build Status](https://travis-ci.org/gesof/ansible-role-aerospike.svg?branch=master)](https://travis-ci.org/gesof/ansible-role-aerospike)

Installs the [Aerospike NoSQL database](https://aerospike.com/) on RedHat/CentOS or Debian/Ubuntu Linux.

## Requirements

Requires the EPEL repository on RedHat/CentOS (you can install it using the `geerlingguy.repo-epel` role).

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    aerospike_package_name: "aerospike"

Aerospike package name you want to install. See `apt-cache policy aerospike` or `yum list aerospike` for a listing of available candidates.

    aerospike_version: "5.6.0.5"

Aerospike version that should be installed. See the [Aerospike repositories](https://download.aerospike.com/download/server/notes.html) for a listing of available versions. Some examples include: `5.6.0.5`, `5.5.0.12`, `5.4.0.14` and `4.9.0.33`.

    aerospike_config_path: /etc/aerospike

The path in which Aerospike configuration files will be stored.

    aerospike_listen_address: ""
    aerospike_listen_port: "3000"

The address and port on which Aerospike will listen. The defaults tell Aerospike to listen on all interfaces on port 3000, but you can specify an address and/or alternate port if desired.

    aerospike_admin_listen_host: "127.0.0.1"
    aerospike_admin_listen_port: "3003"

The host and port through which Aerospike will accept admin requests For more information, see [asinfo documentation](https://docs.aerospike.com/docs/tools/asinfo)).

    aerospike_storage: "file,/opt/aerospike/data/bar.data"
How Aerospike stores cache entries.

    aerospike_pidfile: /var/run/aerospike/asd.pid

Aerospike PID file path. Set to an empty string if you don't want to use a PID file.

    aerospike_extra_options: ""

Extra options or flags to pass to the Aerospike daemon when it starts.

    aerospike_enabled_services:
      - aerospike

Services that will be started at boot and should be running after this role is complete. If set to an empty array, no services will be enabled at startup.

## Dependencies

    For Aerospike Server 5.1 and later, libcurl is required.

## Example Playbook

    - hosts: webservers
      vars_files:
        - vars/main.yml
      roles:
        - gesof.aerospike

*Inside `vars/main.yml`*:

    aerospike_service_addresses: "any"
    aerospike_default_backend_port: 3000
    ... etc ...

## License

MIT / BSD

## Author Information

This role was created in 2021 by [Gesof](https://github.com/gesof).
