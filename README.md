# nomachine

Ansible role to install and configure [NoMachine](https://www.nomachine.com/) remote desktop on Debian/Ubuntu systems.

## Requirements

- Debian or Ubuntu host
- `become: true` privileges (sudo)

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `nomachine_deb_url` | `https://www.nomachine.com/free/linux/64/deb` | URL to download the `.deb` package from |
| `nomachine_deb_file` | `nomachine.deb` | Filename used when saving the package to `/tmp` |
| `nomachine_service_name` | `nxserver` | Name of the systemd service to enable and start |

## Example Playbook

```yaml
- hosts: all
  become: true
  roles:
    - role: nomachine
```

Override variables if needed:

```yaml
- hosts: all
  become: true
  roles:
    - role: nomachine
      vars:
        nomachine_deb_url: "https://www.nomachine.com/free/linux/64/deb"
        nomachine_service_name: "nxserver"
```

## Manual setup (without Ansible)

The default download is for 64-bit Linux:

```bash
curl -fL https://www.nomachine.com/free/linux/64/deb -o /tmp/nomachine.deb
sudo apt install /tmp/nomachine.deb
rm /tmp/nomachine.deb
sudo systemctl enable --now nxserver
```

## License

MIT

## Author

Varssos
