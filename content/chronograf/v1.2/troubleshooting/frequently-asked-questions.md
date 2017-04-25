---
title: Frequently Asked Questions (FAQ)
menu:
  chronograf_1_2:
    weight: 0
    parent: Troubleshooting
---

* [What Kapacitor event handlers are supported in Chronograf?](#what-kapacitor-event-handlers-are-supported-in-chronograf)
* [What applications are supported in Chronograf?](#what-applications-are-supported-in-chronograf)
* [How do I connect Chronograf to an InfluxEnterprise cluster?](#how-do-i-connect-chronograf-to-an-influxenterprise-cluster)
* [What does the status column indicate on the Host List page?](#what-does-the-status-column-indicate-on-the-host-list-page)
* [Why is my host's status red when data are still arriving?](#why-is-my-host-s-status-red-when-data-are-still-arriving)

## What Kapacitor event handlers are supported in Chronograf?

Chronograf integrates with [Kapacitor](/kapacitor/v1.2/), InfluxData's data processing platform, to send alert messages to event handlers.
Chronograf supports the following event handlers:

* Alerta
* Exec
* HipChat
* HTTP/Post
* OpsGenie
* PagerDuty
* Sensu
* Slack
* SMTP/Email
* Talk
* Telegram
* TCP
* VictorOps

To configure a Kapacitor event handler in Chronograf, [install Kapacitor](/chronograf/v1.2/introduction/getting-started/#kapacitor-setup) and [connect it to Chronograf](/chronograf/v1.2/introduction/getting-started/#4-connect-chronograf-to-kapacitor).
The Configure Kapacitor page includes the event handler configuration options; see the [Configure Kapacitor Event Handlers](/chronograf/v1.2/guides/configure-kapacitor-event-handlers/) guide for more information.

## What applications are supported in Chronograf?

Chronograf offers pre-created dashboards for several [Telegraf](/telegraf/v1.2/) input plugins/applications.
We list those applications below and link to their Telegraf documentation:

* [Apache](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/apache)
* [Consul](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/consul)
* [Docker](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/docker)
* [Elastic](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/elasticsearch)
* etcd
* [HAProxy](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/haproxy)
* IIS
* [InfluxDB](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/influxdb)
* [Kubernetes](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/kubernetes)
* [Memcached](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/memcached)
* [Mesos](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/mesos)
* [MongoDB](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/mongodb)
* [MySQL](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/mysql)
* Network
* [NGINX](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/nginx)
* [NSQ](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/nsq)
* [Ping](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/ping)
* [PostgreSQL](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/postgresql)
* Processes
* [RabbitMQ](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/rabbitmq)
* [Redis](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/redis)
* [Riak](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/riak)
* [System](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/system/SYSTEM_README.md)
    * [CPU](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/system/CPU_README.md)
    * [Disk](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/system/DISK_README.md)
    * [DiskIO](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/system/disk.go#L136)
    * [Memory](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/system/MEM_README.md)
    * [Net](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/system/net.go)
    * [Netstat](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/system/NETSTAT_README.md)
    * [Processes](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/system/PROCESSES_README.md)
    * [Procstat](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/procstat/README.md)
* [Varnish](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/varnish)
* [Windows Performance Counters](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/win_perf_counters)

Enable and disable applications in your [Telegraf configuration file](https://github.com/influxdata/telegraf/blob/master/etc/telegraf.conf).
See the [Telegraf Configuration](https://github.com/influxdata/telegraf/blob/master/docs/CONFIGURATION.md) documentation for more information.

## How do I connect Chronograf to an InfluxEnterprise cluster?

The connection details form requires additional information when connecting Chronograf to an [InfluxEnterprise cluster](https://docs.influxdata.com/enterprise/v1.2/).

When you enter InfluxDB's HTTP bind address in the `Connection String` input, Chronograf automatically checks if that InfluxDB instance is a data node.
If it is a data node, Chronograf automatically adds the `Meta Service Connection URL` input to the connection details form.
Enter the HTTP bind address of one of your cluster's meta nodes into that input and Chronograf takes care of the rest.

![Cluster connection details](/img/chronograf/v1.2/faq-cluster-connection.png)

Note that the example above assumes that you do not have authentication enabled.
If you have authentication enabled, the form requires username and password information.
For more details about monitoring an InfluxEnterprise cluster, see the [Monitor an InfluxEnterprise Cluster](/chronograf/v1.2/guides/monitor-an-influxenterprise-cluster/) guide.

## What does the status column indicate on the Host List page?
## Why is my host's status red when data are still arriving?


