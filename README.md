# Ansible Role: Ghostwriter ([Ludus](https://ludus.cloud))

An Ansible Role that installs [Ghostwriter](https://github.com/GhostManager/Ghostwriter) on a Linux-based host using ghostwriter-cli and Docker Compose.

## Requirements

A Debian (buster, bullseye, bookworm) or Ubuntu (bionic, focal, jammy) host.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# Installation directory for Ghostwriter
ludus_ghostwriter_install_path: "/opt/ghostwriter"

# Deploy a dev environment (no TLS certificates, debug logging enabled)
ludus_ghostwriter_development_mode: true

# Automatically allow the host's IP address
ludus_ghostwriter_allow_host_ip: true
```

## Dependencies

- `geerlingguy.docker` 

## Example Playbook

```yaml
- hosts: ghostwriter_hosts
  roles:
    - 5tuk0v.ludus_ghostwriter
  vars:
    - ludus_ghostwriter_development_mode: false
```

## Example Ludus Range Config

```yaml
ludus:
  - vm_name: "{{ range_id }}-gw-ubuntu2204-x64"
    hostname: "{{ range_id }}-gw"
    template: ubuntu-22.04-x64-server-template
    vlan: 10
    ip_last_octet: 10
    ram_gb: 2
    cpus: 2
    linux: true
    roles:
      - 5tuk0v.ludus_ghostwriter
    role_vars:
      ludus_ghostwriter_install_path: "/opt/ghostwriter"
      ludus_ghostwriter_development_mode: true
```

## License

GPLv3

## Author Information

This role was created by [5tuk0v](https://github.com/5tuk0v), for [Ludus](https://ludus.cloud/).

- GitHub: [@5tuk0v](https://github.com/5tuk0v)
- Twitter/X: [@stuk0v_](https://twitter.com/stuk0v_)
