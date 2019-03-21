# Ansible role for Telegraf

[![CircleCI](https://circleci.com/gh/angristan/ansible-telegraf.svg?style=svg)](https://circleci.com/gh/angristan/ansible-telegraf)

This is a simple role that will install Telegraf from the InfluxDB APT repo and configure it.

All the configuration is done with the `telegraf.conf.j2` template.

It's partly reusable for now, it's WIP.

## Sample playbook

```yaml
---

- hosts: myhost
  roles:
    - name: telegraf
      tags: telegraf
  vars:
    telegraf_output_type: influxdb
    telegraf_output_host: "{{ influxdb_host }}"
    telegraf_output_database: telegraf
    telegraf_output_username: telegraf
    telegraf_output_password: "{{ vault_telegraf_output_password }}"
    telegraf_cpu_enabled: true
    telegraf_mem_enabled: true
    telegraf_dns_query_enabled: true
    telegraf_dns_query_servers:
      - 127.0.0.1
      - 1.1.1.1
      - 8.8.8.8
```
