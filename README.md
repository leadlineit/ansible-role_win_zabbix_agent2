
---

# Ansible Galaxy role for installing and configuring Zabbix Agent2 on Windows Server

![Build Status](https://github.com/leadlineit/ansible-role-win_zabbix_agent2/actions/workflows/ansible-galaxy-ci.yml/badge.svg)  
[![Galaxy Role](https://img.shields.io/badge/Ansible--Galaxy-leadlineit.win_zabbix_agent2-blue.svg?logo=ansible&logoColor=white)](https://galaxy.ansible.com/leadlineit/win_zabbix_agent2/)

This role helps to install and configure Zabbix Agent2 on Windows Server (2016/2019/2022).

---

## Requirements

This role requires:
- **Ansible 2.11 or higher**
- **Windows Server** with support for Windows Containers.

---

## Role Variables

The variables that can be passed to this role and a brief description about them are as follows:

```yaml
---
zabbix_server: "your.zabbix.server"             # Address of the Zabbix Server
zabbix_server_active: "your.zabbix.server"      # Address of the Active Zabbix Server
zabbix_listenPort: "10050"                      # Listening port for Zabbix Agent2
```

These variables are optional and have default values defined in `defaults/main.yml`:
```yaml
---
zabbix_server: "default.zabbix.server"
zabbix_server_active: "default.zabbix.server"
zabbix_listenPort: "10050"
```

If you do not provide custom values, the role will use these defaults.

---

## Tasks Overview

### Installation:
1. Download and install Zabbix Agent2 MSI package from the official repository.
2. Configure the service to run automatically.

### Configuration:
1. Deploy a custom configuration file for Zabbix Agent2.
2. Replace default settings with values provided via role variables.
3. Restart the Zabbix Agent2 service if configuration changes are detected.

### Firewall Rules:
1. Remove the default Zabbix Agent2 firewall rule.
2. Add a custom rule allowing traffic to the port defined in `zabbix_listenPort`.

---

## Dependencies

None.

---

## Example Playbook

Below is an example of how to use this role in your playbook:

```yaml
- hosts: windows
  roles:
    - role: leadlineit.win_zabbix_agent2
      zabbix_server: "zabbix.example.com"
      zabbix_server_active: "zabbix.example.com"
      zabbix_listenPort: "10500"
```

---

## Tags

You can use the following tags to run specific tasks of the role:
- **`install_zabbix_agent2`** — Run tasks related to the installation of Zabbix Agent2.
- **`configure_zabbix_agent2`** — Run tasks related to configuration and firewall settings.

Example:
```bash
ansible-playbook playbook.yml --tags install_zabbix_agent2
```

---

## License

MIT

---

## Author Information

This role was created by **Dmytro Fedorov**.


---
