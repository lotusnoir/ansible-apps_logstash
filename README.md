# Ansible Role: ansible-apps_logstash


## Description

[![Build Status](https://travis-ci.com/lotusnoir/ansible-apps_logstash.svg?branch=master?style=flat)](https://travis-ci.com/lotusnoir/ansible-apps_logstash)
[![License](https://img.shields.io/badge/license-Apache--2.0-brightgreen?style=flat)](https://opensource.org/licenses/Apache-2.0)
[![Ansible Role](https://img.shields.io/badge/galaxy-apps_logstash-purple?style=flat)](https://galaxy.ansible.com/lotusnoir/apps_logstash)
![GitHub repo size](https://img.shields.io/github/repo-size/lotusnoir/ansible-apps_logstash?color=orange&style=flat)
![Ansible Quality Score](https://img.shields.io/ansible/quality/52300)
[![downloads](https://img.shields.io/ansible/role/d/52300)](https://galaxy.ansible.com/lotusnoir/apps_logstash)
[![Version](https://img.shields.io/github/release/lotusnoir/ansible-apps_logstash.svg)](https://github.com/lotusnoir/ansible-apps_logstash/releases/)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-apps_logstash&metric=alert_status)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-apps_logstash)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-apps_logstash&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-apps_logstash)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-apps_logstash&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-apps_logstash)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-apps_logstash&metric=security_rating)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-apps_logstash)

Deploy [logstash](https://www.elastic.co/fr/logstash) app using ansible.


## Requirements

You nee to install java, we use:

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

This project is licensed under Apache License. See [LICENSE](/LICENSE) for more details.
