elasticsearch
=============

A role to manage [elasticsearch](https://www.elastic.co/).

Requirements
------------

No external dependencies.

Role Variables
--------------

For details on configuring Elasticsearch, refer to their
[documentation](http://www.elastic.co/guide/en/elasticsearch/reference/current/index.html).

- **elasticsearch_version**: Version number of *elasticsearch* to
  deploy.  Defaults to `1.1`.
- **elasticsearch_user**: User elasticsearch runs as.  Defaults to `elasticsearch`.
- **elasticsearch_nofile**: Number of files *elasticsearch* user can
  open.  Defaults to `32000`.
- **elasticsearch_cluster_name**: The cluster name.  Defaults to `elasticsearch`.
- **elasticsearch_node_name**: The node name.  Defaults to the node's FQDN.
- **elasticsearch_is_node_master**: Whether to allow this node to be
  eligible as master.  Defaults to `yes`.
- **elasticsearch_is_node_data**: Whether to allow this node to store
  data.  Defaults to `yes`.
- **elasticsearch_index_number_of_shards**: Number of shards of an
  index.  Defaults to `5`.
- **elasticsearch_index_number_of_shards**: Number of replicas of an
  index.  Defaults to `1`.
- **elasticsearch_bootstrap_mlockall**:  Whether to lock JVM memory.
  Defaults to `yes`.
- **elasticsearch_network_host**: The IP address to use for *bind* and
  *publish*.  Defaults to Ansible's fact *ansible_default_ipv4.address*.
- **elasticsearch_http_host**: The IP address to use for elasticsearch
  APIs over HTTP for *bind* and *publish*.  Defaults to Ansible's fact
  *ansible_default_ipv4.address*.
- **elasticsearch_minimum_master_nodes**:  The minimum number of master
  nodes.  Defaults to `1`.  On clusters with more than 2 nodes, this
  should be higher than 1.
- **elasticsearch_plugin_mandatory**: The mandatory plugins for
  Elasticsearch.  Defaults to `paramedic,head`.
- **elasticsearch_plugins**:  A list of dictionaries that describe
  plugins to install.  The keys are the *name* and *path*.  The default
  is:
```
  elasticsearch_plugins:
  - { name: 'paramedic', path: 'karmi/elasticsearch-paramedic' }
  - { name: 'head',      path: 'mobz/elasticsearch-head'       }
```
- **elasticsearch_path_conf**: The configuration directory for
  Elasticsearch.  Defaults to `/etc/elasticsearch`.
- **elasticsearch_path_data**: The directory to store index data.
  Defaults to `/var/lib/elasticsearch`.
- **elasticsearch_path_work**: The path to temporary files.  Defaults to `/tmp/elasticsearch`.
- **elasticsearch_path_logs**: The path to log files.  Defaults to `/var/log/elasticsearch`.
- **elasticsearch_path_home**: The path to where Elasticsearch binaries
  are installed.  Defaults to `/usr/share/elasticsearch`.
- **elasticsearch_path_plugins**: The path where plugins are installed.
  Defaults to `/usr/share/elasticsearch/plugins`.
- **elasticsearch_java_opts**: Options to pass to JVM.  Defaults to
  empty string.
- **elasticsearch_java_heap_size**: Size of JVM heap size.  Defaults to
  40% of total host memory.

Dependencies
------------

No dependency on other roles.

Example Playbook
----------------

A trivial example:

    - hosts: servers
      roles:
         - { role: sfromm.elasticsearch }

License
-------

GPLv2

Author Information
------------------

See https://github.com/sfromm
