# Ansible Role: ansible-apps_logstash


## Description

[![Build Status](https://travis-ci.com/lotusnoir/ansible-apps_logstash.svg?branch=master)](https://travis-ci.com/lotusnoir/ansible-apps_logstash)[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)[![Ansible Role](https://img.shields.io/badge/ansible%20role-apps__logstash-blue)](https://galaxy.ansible.com/lotusnoir/ansible-apps_logstash/)[![GitHub tag](https://img.shields.io/badge/version-latest-blue)](https://github.com/lotusnoir/ansible-apps_logstash/tags)

Deploy [logstash](https://www.elastic.co/fr/logstash) app using ansible.


## Requirements

In the meta dependencies we use:

 - geerlingguy.java

## Role variables

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `logstash_version` | 6.x | logstash version |
| `logstash_dir` | /usr/share/logstash | install directory |
| `logstash_install_plugins` | [] | list of installed plugins |
| `logtstash_log_dir` | /var/log/logstash | log directory |
| `logtstash_log_level` | info | log level  |
| `logtstash_path_data` | /var/lib/logstash |  |
| `logtstash_workers` | 12 |  |
| `logtstash_batch_size` | 500 |  |
| `logstash_heap_size_initial` | 2 | java initial heap size |
| `logstash_heap_size_max` | 3 | java max heap size |
| `logstash_rules_files` | [] | rules conf file to load |
| `logstash_pipelines` | "/etc/logstash/conf.d/*.conf" | pipelines for config files |

## Examples

	---
	- hosts: apps_logstash
	  become: yes
	  become_method: sudo
	  gather_facts: yes
	  roles:
	    - role: ansible-apps_logstash
	  vars:
        logstash_install_plugins: []
          - logstash-input-snmptrap
          - logstash-output-gelf
          - logstash-output-kafka
          - logstash-output-slack
          - logstash-output-email
          - logstash-output-tcp
        logstash_rules_files: []
          - conf.d/*.conf
	  environment: 
	    http_proxy: "{{ http_proxy }}"
	    https_proxy: "{{ https_proxy }}"
	    no_proxy: "{{ no_proxy }}


## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
