# telegraf-influxdbproxy-ansible

Ansible role to install and configure telegraf as a InfluxDB proxy which listens v1 locally and outputs v2 to InfluxDB Cloud

## Created for personal use and tested with 

* RaspberryPi OS Lite (32-bit)
* RaspberryPi ZeroW 2

## Role Variables

### Mandatory

* `telegraf_output_influxdbv2` (dict, default null)
    * required dict values as strings are `url`, `token`, `organization` and `bucket`

### Optional

* `ruuviproxy_telegraf_interval` (string, default "20s")
* `ruuviproxy_telegraf_round_interval` (boolean, default true)
* `ruuviproxy_telegraf_metric_batch_size` (int, default 1000)
* `ruuviproxy_telegraf_metric_buffer_limit` (int, default 10000)
* `ruuviproxy_telegraf_collection_jitter` (string, default "0s")
* `ruuviproxy_telegraf_flush_interval` (string, default "10s")
* `ruuviproxy_telegraf_flush_jitter` (string, default "0s")
* `ruuviproxy_telegraf_log_timezone` (string, default "Europe/Helsinki")
* `ruuviproxy_telegraf_influxdb_listener` (string, default ":8186")

## Example usage

ansible.cfg
```
[defaults]
roles_path = roles
```

requirements.yml
```
- src: https://github.com/hulkk/telegraf-influxdbproxy-ansible
```

`ansible-galaxy install -r requirements.yml --force`

site.yml
```
- hosts: ruuvi
  roles:
     - telegraf-influxdbproxy-ansible
```

