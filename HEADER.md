# ansible-role-promtail

[![Mocelule Test Status](https://github.com/Grokon/ansible-role-promtail/actions/workflows/molecule.yaml/badge.svg?branch=master)](https://github.com/Grokon/ansible-role-promtail/actions/workflows/molecule.yaml)
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
