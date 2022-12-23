# ansible-role-promtail

[![Mocelule Test Status](https://github.com/Grokon/ansible-role-promtail/actions/workflows/molecule.yml/badge.svg?branch=master)](https://github.com/Grokon/ansible-role-promtail/actions/workflows/molecule.yml)
[![GitHub release](https://img.shields.io/github/release/Grokon/ansible-role-promtail.svg)](https://github.com/Grokon/ansible-role-promtail/release)
[![GitHub license](https://img.shields.io/github/license/Grokon/ansible-role-promtail.svg)](https://github.com/Grokon/ansible-role-promtail/blob/master/LICENSE)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-grokon.promtail-blue.svg)](https://galaxy.ansible.com/grokon/promtail/)

## Example Playbook

```yaml
- hosts: all
  roles:
    - grokon.promtail
  vars:
    promtail__loki_server_domain: my_loki_instance
    promtail__scrape_configs:
      - job_name: syslog
        static_configs:
          - targets:
              - localhost
            labels:
              job: syslog
              host: "{{ ansible_host }}"
              __path__: /var/log/syslog
```

An Ansible Role that installs promtail on Debian

## Table of content

- [Default Variables](#default-variables)
  - [promtail__config_clients](#promtail__config_clients)
  - [promtail__config_dir](#promtail__config_dir)
  - [promtail__config_file](#promtail__config_file)
  - [promtail__config_file_sd_dir](#promtail__config_file_sd_dir)
  - [promtail__config_positions](#promtail__config_positions)
  - [promtail__config_server](#promtail__config_server)
  - [promtail__install](#promtail__install)
  - [promtail__log_level](#promtail__log_level)
  - [promtail__loki_server_url](#promtail__loki_server_url)
  - [promtail__path](#promtail__path)
  - [promtail__scrape_configs](#promtail__scrape_configs)
  - [promtail__target_config](#promtail__target_config)
  - [promtail__tmp_dir](#promtail__tmp_dir)
  - [promtail__url](#promtail__url)
  - [promtail__version](#promtail__version)
- [Discovered Tags](#discovered-tags)
- [Open Tasks](#open-tasks)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Default Variables

### promtail__config_clients

Promtail clients config

#### Default value

```YAML
promtail__config_clients:
  - url: '{{ promtail__loki_server_url }}/loki/api/v1/push'
```

### promtail__config_dir

Promtail configurations directory

#### Default value

```YAML
promtail__config_dir: /etc/promtail
```

### promtail__config_file

Promtail config file path

#### Default value

```YAML
promtail__config_file: '{{ promtail__config_dir }}/config.yml'
```

### promtail__config_file_sd_dir

Promtail file_sd directory

#### Default value

```YAML
promtail__config_file_sd_dir: '{{ promtail__config_dir }}/file_sd'
```

### promtail__config_positions

Promtail positions config

#### Default value

```YAML
promtail__config_positions:
  filename: '{{ promtail__config_dir }}/positions.yaml'
```

### promtail__config_server

Promtail server config, listen on - for metrics

#### Default value

```YAML
promtail__config_server:
  http_listen_port: 9080
```

### promtail__install

Weather of not to install promtail Set to false if it's already installed and wanted to remove it

#### Default value

```YAML
promtail__install: true
```

### promtail__log_level

Promtail log level. One of: debug, info, warn, error

#### Default value

```YAML
promtail__log_level: warn
```

### promtail__loki_server_url

Promtail loki server url

#### Default value

```YAML
promtail__loki_server_url: http://localhost:3100
```

### promtail__path

Default path for promtail

#### Default value

```YAML
promtail__path: /usr/local/bin/promtail
```

### promtail__scrape_configs

Promtail scrape configurations

#### Default value

```YAML
promtail__scrape_configs: []
```

#### Example usage

```YAML
Example:
promtail__scrape_configs:
- job_name: syslog
  static_configs:
    - targets:
      - localhost
      labels:
        job: syslog
        host: "{{ ansible_host }}"
        __path__: /var/log/syslog
```

### promtail__target_config

#### Default value

```YAML
promtail__target_config: {}
```

### promtail__tmp_dir

TMP directory for download promtail

#### Default value

```YAML
promtail__tmp_dir: /tmp
```

### promtail__url

Promtail target config

#### Default value

```YAML
promtail__url: https://github.com/grafana/loki/releases/download/v{{ promtail__version
  }}/promtail-linux-amd64.zip
```

#### Example usage

```YAML
 promtail_target_config:
   sync_period: "10s"
```

### promtail__version

Default to latest version, pin version example 2.6.1

#### Default value

```YAML
promtail__version: latest
```

## Discovered Tags

**_promtail_configure_**

**_promtail_install_**

**_promtail_run_**

## Open Tasks

- (improvement): Add variables for logs

## Dependencies

None.

## License

MIT

## Author

grokon
