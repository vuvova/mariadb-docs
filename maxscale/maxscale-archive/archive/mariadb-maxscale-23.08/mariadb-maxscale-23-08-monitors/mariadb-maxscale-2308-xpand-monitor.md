# MaxScale 23.08 Xpand Monitor

## Xpand Monitor

## Xpand Monitor

### Overview

The Xpand Monitor is a monitor that monitors a Xpand cluster. It is\
capable of detecting the cluster setup and creating corresponding server\
instances within MaxScale.

### Required Grants

The monitor user _must_ have the following grants:

```
CREATE USER 'maxscale'@'maxscalehost' IDENTIFIED BY 'maxscale-password';
GRANT SELECT ON system.membership TO 'maxscale'@'maxscalehost';
GRANT SELECT ON system.nodeinfo TO 'maxscale'@'maxscalehost';
GRANT SELECT ON system.softfailed_nodes TO 'maxscale'@'maxscalehost';
```

Further, if you want be able to _softfail_ and _unsoftfail_ a node via MaxScale,\
then the monitor user must have `SUPER` privileges:

```
GRANT SUPER ON *.* TO 'maxscale'@'maxscalehost';
```

### Configuration

A minimal configuration for a monitor requires one server in the Xpand\
cluster, and a username and a password to connect to the server. Note that\
by default the Xpand monitor will only use that server in order to\
dynamically find out the configuration of the cluster; after startup it\
will completely rely upon information obtained at runtime. To change the\
default behaviour, please see the parameter [dynamic\_node\_detection](mariadb-maxscale-2308-xpand-monitor.md#dynamic_node_detection).

To ensure that the Xpand monitor will be able to start, it is adviseable\
to provide _more_ than one server to cater for the case that not all nodes\
are always up when MaxScale starts.

**Note:** All services that use servers monitored by xpandmon should use\
the `cluster` parameter to define the set of servers they use. This will\
guarantee that the services use servers that are valid members of the\
XPand cluster.

```
[TheXpandMonitor]
type=monitor
module=xpandmon
servers=server1,server2,server3
user=myuser
password=mypwd

[MyService]
type=service
router=readconnroute
cluster=TheXpandMonitor
user=myuser
password=mypwd
```

### Dynamic Servers

The server objects the Xpand monitor creates for each detected\
Xpand node will be named like

```
@@<name-of-xpand-monitor>:node-<id>
```

where `<name-of-xpand-monitor>` is the name of the Xpand monitor\
instance, as defined in the MaxScale configuration file, and `<id>` is the\
id of the Xpand node.

For instance, with the Xpand monitor defined as above and a Xpand\
cluster consisting of 3 nodes whose ids are `1`, `2` and `3` respectively,\
the names of the created server objects will be:

```
@@TheXpandMonitor:node-1
@@TheXpandMonitor:node-2
@@TheXpandMonitor:node-3
```

When dynamic servers are created, the values for the configuraton settings`max_routing_connections`, `persistmaxtime`, `persistpoolmax` and`proxy_protocol` are copied from the settings of the bootstrap servers.\
Note that the values of these settings must be **identical** on every\
bootstrap server.

### Common Monitor Parameters

For a list of optional parameters that all monitors support, read the [Monitor Common](mariadb-maxscale-2308-common-monitor-parameters.md) document.

### Xpand Monitor optional parameters

These are optional parameters specific to the Xpand Monitor.

#### `cluster_monitor_interval`

* Type: [duration](../mariadb-maxscale-23-08-getting-started/mariadb-maxscale-2308-mariadb-maxscale-configuration-guide.md#durations)
* Mandatory: No
* Dynamic: Yes
* Default: `60s`

Defines how often the monitor checks the state of the entire cluster. The\
default value is 60 seconds, which should not be lowered as that may have\
an adverse effect on the Cluster itself.

```
cluster_monitor_interval=120s
```

#### `health_check_threshold`

* Type: count
* Mandatory: No
* Dynamic: Yes
* Default: `2`

Defines how many times the health check may fail before the monitor\
considers a particular node to be down.

```
health_check_threshold=3
```

#### `dynamic_node_detection`

* Type: [boolean](../mariadb-maxscale-23-08-getting-started/mariadb-maxscale-2308-mariadb-maxscale-configuration-guide.md#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `true`

By default, the Xpand monitor will only use the bootstrap nodes\
in order to connect to the Xpand cluster and then find out the\
cluster configuration dynamically at runtime.

That behaviour can be turned off with this optional parameter, in\
which case all Xpand nodes must manually be defined as shown below.

```
[Node-1]
type=server
address=192.168.121.77
port=3306
...

[Node-2]
...

[Node-3]
...

[TheXpandMonitor]
type=monitor
module=xpandmon
servers=Node-1, Node-2, Node-3
dynamic_node_detection=false
```

The default value of `dynamic_node_detection` is `true`.

See also [health\_check\_port](mariadb-maxscale-2308-xpand-monitor.md#health_check_port).

#### `health_check_port`

* Type: integer
* Mandatory: No
* Dynamic: Yes
* Default: `3581`

With this optional parameter it can be specified what health check\
port to use, if `dynamic_node_detection` has been disabled.

```
health_check_port=4711
```

Note that this parameter is _ignored_ unless `dynamic_node_detection`\
is `false`. Note also that the port must be the same for all nodes.

#### `region_name`

* Type: string
* Mandatory: No
* Dynamic: Yes
* Default: ''

Mutually exclusive with `region_oid`.

`region_name` speficies the name of the region the instance MaxScale is\
running in. Should be specified only if Xpand Multi-Region HA cluster,\
which is available from Xpand 23.08 onwards, is used. With `region_name`\
specified, MaxScale will only consider nodes from that region.

#### `region_oid`

* Type: integer
* Mandatory: No
* Dynamic: Yes
* Default: ''

Mutually exclusive with `region_name`.

`region_oid` speficies the oid of the region the instance MaxScale is\
running in. Should be specified only if Xpand Multi-Region HA cluster,\
which is available from Xpand 23.08 onwards, is used. With `region_oid`\
specified, MaxScale will only consider nodes from that region.

### Commands

The Xpand monitor supports the following module commands.

#### `softfail`

With the `softfail` module command, a node can be _softfailed_ via\
MaxScale. The command requires as argument the name of the Xpand\
monitor instance (as defined in the configuration file) and the name\
of the node to be softfailed.

For instance, with a configuration file like

```
[TheXpandMonitor]
type=monitor
module=xpandmon
...
```

then the node whose server name is `@@TheXpandMonitor:node-1` can\
be softfailed like

```
$ maxctrl call command xpandmon softfail TheXpandMonitor @@TheXpandMonitor:node-1
```

If the softfailing of a node is successfully initiated, then the status\
of the corresponding MaxScale server object will be set to `Draining`,\
which will prevent new connections from being created to the node.

When the number of connections through MaxScale to the node has dropped\
to 0, its state will change to `Drained`. Note that the state `Drained`\
only tells that there are no connections to the node, not what the state\
of the softfailing operation is.

#### `unsoftfail`

With the `unsoftfail` module command, a node can be _unsoftfailed_ via\
MaxScale. The command requires as argument the name of the Xpand\
monitor instance (as defined in the configuration file) and the name\
of the node to be unsoftfailed.

With a setup similar to the `softfail` case, a node can be unsoftfailed\
like:

```
$ maxctrl call command xpandmon unsoftfail TheXpandMonitor @@TheXpandMonitor:node-1
```

If a node is successfully softfailed, then a `Draining` status of\
the corresponding MaxScale server object will be cleared.

### SOFTFAILed nodes

During the cluster check, which is performed once per`cluster_monitor_interval`, the monitor will also check whether any\
nodes are being softfailed. The status of the corresponding server\
object of a node being softfailed will be set to `Draining`,\
which will prevent new connections from being created to that node.

When the number of connections through MaxScale to the node has dropped\
to 0, its state will change to `Drained`. Note that the state `Drained`\
only tells that there are no connections to the node, not what the state\
of the softfailing operation is.

If a node that was softfailed is UNSOFTFAILed then the `Draining`\
status will be cleared.

If the softfailing and unsoftfailing is initiated using the `softfail`\
and `unsoftfail` commands of the Xpand monitor, then there will be\
no delay between the softfailing or unsoftfailing being initiated and the`Draining` status being turned on/off.

CC BY-SA / Gnu FDL
