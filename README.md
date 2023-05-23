# ansible-apps_logstash

[![Galaxy Role](https://img.shields.io/badge/galaxy-apps_logstash-purple?style=flat)](https://galaxy.ansible.com/lotusnoir/apps_logstash)
[![Version](https://img.shields.io/github/release/lotusnoir/ansible-apps_logstash.svg)](https://github.com/lotusnoir/ansible-apps_logstash/releases/latest)
[![GitHub repo size](https://img.shields.io/github/repo-size/lotusnoir/ansible-apps_logstash?color=orange&style=flat)](https://galaxy.ansible.com/lotusnoir/apps_logstash)
[![downloads](https://img.shields.io/ansible/role/d/56094)](https://galaxy.ansible.com/lotusnoir/apps_logstash)
[![Ansible Quality Score](https://img.shields.io/ansible/quality/56094)](https://galaxy.ansible.com/lotusnoir/apps_logstash)
[![License](https://img.shields.io/badge/license-Apache--2.0-brightgreen?style=flat)](https://opensource.org/licenses/Apache-2.0)

## Description

Deploy [logstash](https://www.elastic.co/fr/logstash) app using ansible.
## Requirements

You need to install java - lotusnoir.apps_java

## Role variables

See [variables](/defaults/main.yml) for more details.

## Examples

        ---
        - hosts: apps_logstash
          become: true
          become_method: sudo
          gather_facts: true
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



## License

This project is licensed under Apache License. See [LICENSE](/LICENSE) for more details.

## Author Information

- [Philippe LEAL](https://github.com/lotusnoir)
