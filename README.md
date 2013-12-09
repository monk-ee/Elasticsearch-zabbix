Elasticsearch-zabbix
====================

Elasticsearch template and script for zabbix 2.0

This project is a fork of Elasticsearch template from zabbix-grab-bag

Now forked again - LOL

https://github.com/untergeek/zabbix-grab-bag

These are made available by me under an Apache 2.0 license.

http://www.apache.org/licenses/LICENSE-2.0.html


Dependencies
=============
 - it needs pyes to work https://pypi.python.org/pypi/pyes/
 - pyes is a connector to use elasticsearch from python.


How it works for Debian/Ubuntu (at least)
=============

- Put ESzabbix.py in /etc/zabbix/externalscripts/ in the zabbix node

- Put ESzabbix.userparm in the zabbix include parameters dir; "/etc/zabbix/zabbix_agentd.d"

- Import ESzabbix_templates.xml to zabbix server

- Add the following MACRO to the Host when attaching the template:  {$NODENAME}


Specs
=====

The template xml file actually contains three templates:

1. Elasticsearch Node & Cache (which is for node-level monitoring)

2. Elasticsearch Cluster (cluster state, shard-level monitoring, record count, storage sizes, etc.)

3. Elasticsearch Service (ES service status)



There are triggers assigned for the cluster state:

0 = Green (OK)

1 = Yellow (Average, depends on "red")

2 = Red (High)


You will likely want to assign a value mapping for the ElasticSearch Cluster Status item.

In any event, the current list of included items is:

* ES Cluster (11 Items)
	- Cluster-wide records indexed per second
	- Cluster-wide storage size
	- ElasticSearch Cluster Status
	- Number of active primary shards
	- Number of active shards
	- Number of data nodes
	- Number of initializing shards
	- Number of nodes
	- Number of relocating shards
	- Number of unassigned shards
	- Total number of records
* ES Cache (2 Items)
	- Node Field Cache Size
	- Node Filter Cache Size
* ES Node (2 Items)
	- Node Storage Size
	- Records indexed per second
* ES Service (1 Item)
	- Elasticsearch service status
