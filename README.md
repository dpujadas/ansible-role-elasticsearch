elasticsearch
=============

This role installs and configures [ElasticSearch](https://www.elastic.co/products/elasticsearch).

Role Variables
--------------

- `elasticsearch_major_version`: ElasticSearch major version to install (default: '2')
- `elasticsearch_config`: Dict with ElasticSearch config (default: '{}')
- `elasticsearch_init_system`: OS init system. Docker phusion/baseimage uses 'runit'. (default 'upstart')

Dependencies
------------

- dpujadas/ansible-role-java

Example Playbook
----------------

    - hosts: servers
      vars:
        elasticsearch_default_options:
          ES_STARTUP_SLEEP_TIME: '5'
        elasticsearch_cluster_name: 'travis-test'
        elasticsearch_config:
          node:
            name: 'travis-docker'
          network:
            host: '0.0.0.0'
        elasticsearch_plugins:
          - name: 'head'
            path: 'mobz/elasticsearch-head'
      roles:
        - {
          role: ansible-role-elasticsearch
        }

License
-------

MIT

[![Build Status](https://travis-ci.org/dpujadas/ansible-role-elasticsearch.svg?branch=master)](https://travis-ci.org/dpujadas/ansible-role-elasticsearch)
