Ansible role: Prometheus Exporter - Chrony
==========================================

Install and configure Chrony Exporter for Prometheus.

Requirements
------------

This role depends on the [base prometheus exporter role](https://github.com/wandansible/prometheus_exporter).

Role Variables
--------------

```
ENTRY POINT: *main* - Install and configure Chrony Exporter for Prometheus

Options (= indicates it is required):

- chrony_exporter_arch_map  Mapping of the possible values of ansible_architecture to the
                             exporter package architectures
          default: null
          type: dict

- chrony_exporter_archive_urls  Override the list of exporter archive urls for different platforms
                                 and architectures
          default: null
          elements: str
          type: list

- chrony_exporter_bin_dir  Directory for the exporter executable
          default: null
          type: str

- chrony_exporter_binary  Filename for the exporter executable
          default: null
          type: str

- chrony_exporter_checksum_type  The exporter package checksum type
          default: null
          type: str

- chrony_exporter_checksum_url  Override the URL for the exporter checksum file
          default: null
          type: str

- chrony_exporter_checksums  Override exporter archive checksums file contents
          default: null
          type: str

- chrony_exporter_clean_src_dir  Remove old downloaded archive files from exporter src directory
          default: true
          type: bool

- chrony_exporter_configure_caddy  If true, configure caddy to add a TLS endpoint for the exporter
          default: false
          type: bool

- chrony_exporter_description  Description for the exporter systemd service
          default: null
          type: str

- chrony_exporter_disabled_collectors  List of collectors to disable
          default: null
          elements: str
          type: list

- chrony_exporter_enabled_collectors  List of collectors to enable
          default: null
          elements: str
          type: list

- chrony_exporter_extra_flags  Extra flags to run exporter with
          default: null
          type: dict

- chrony_exporter_file_sd_dir  Directory, on scrape servers, for the file service discovery target
          default: /etc/prometheus/file_sd/chrony_exporter
          type: str

- chrony_exporter_flags  List of flags to run exporter with, as string or list
          default: null
          type: raw

- chrony_exporter_github_checksum_filename  Filename for the exporter package checksums file on github
          default: null
          type: str

- chrony_exporter_github_org  Name of organisation for exporter github repository
          default: SuperQ
          type: str

- chrony_exporter_github_repo  Name of exporter github repository
          default: null
          type: str

- chrony_exporter_group  Name of the exporter unix group
          default: null
          type: str

- chrony_exporter_groups  Unix groups added to exporter unix user
          default: null
          elements: str
          type: list

- chrony_exporter_handler  Name of the exporter handler to notify
          default: null
          type: str

- chrony_exporter_install  If true, install exporter
          default: true
          type: bool

- chrony_exporter_labels  Labels added to exporter metrics, overrides prometheus_labels
          default: null
          type: dict

- chrony_exporter_listen_addresses  List of addresses and ports to listen on
          default: ['localhost:9123']
          elements: str
          type: list

- chrony_exporter_log_level  Only log messages with the given severity or above
          choices: [debug, info, warn, error]
          default: warn
          type: str

- chrony_exporter_manage_user  If true, add exporter unix user and group
          default: true
          type: bool

- chrony_exporter_port  Listen port
          default: 9123
          type: int

- chrony_exporter_register  If true, register the exporter with the scrape servers
          default: false
          type: bool

- chrony_exporter_scrape_servers  List of servers that scrape exporter metrics from the host,
                                   overrides prometheus_scrape_servers
          default: null
          elements: str
          type: list

- chrony_exporter_service  Name of the exporter systemd service
          default: null
          type: str

- chrony_exporter_service_unit_file  Contents of the systemd unit file for the exporter
          default: null
          type: str

- chrony_exporter_src_dir  Directory for the downloaded exporter src archive
          default: null
          type: str

- chrony_exporter_strip_components  Strip NUMBER leading components from file names on extraction
          default: 1
          type: int

- chrony_exporter_target  Scrape target hostname and port
          default: null
          type: str

- chrony_exporter_user  Name of the exporter unix user
          default: null
          type: str

- chrony_exporter_version  Version to install (use "latest" for the latest version)
          default: latest
          type: str
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/prometheus_exporter,main,wandansible.prometheus_exporter
    ansible-galaxy install git+https://github.com/wandansible/prometheus_exporter.chrony,main,wandansible.prometheus_exporter.chrony
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.prometheus_exporter
      src: https://github.com/wandansible/prometheus_exporter
    - name: wandansible.prometheus_exporter.chrony
      src: https://github.com/wandansible/prometheus_exporter.chrony

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: all
      roles:
         - role: wandansible.prometheus_exporter.chrony
           become: true
