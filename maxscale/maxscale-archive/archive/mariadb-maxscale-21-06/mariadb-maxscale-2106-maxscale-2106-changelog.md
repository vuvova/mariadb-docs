# MaxScale 21.06 Changelog

**NOTE** MaxScale 6.4 was renamed to 21.06 in May 2024. Thus, what would have\
been released as 6.4.16 in June, was released as 21.06.16. The purpose of this\
change is to make the versioning scheme used by all MaxScale series\
identical. 21.06 denotes the year and month when the first 6 release was made.

### MariaDB MaxScale 21.06

* Added `multiplex_timeout`. It sets the time a session can wait\
  for a backend connection to become available when using connection sharing\
  (i.e. `idle_session_pool_time`).
* The `hintrouter` module was removed in MaxScale 21.06.18. The module was non-functional.

For more details, please refer to:

* [MariaDB MaxScale 21.06.19 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-21.06.19-Release-Notes.md)
* [MariaDB MaxScale 21.06.18 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-210618-release-notes-2024-12-09.md)
* [MariaDB MaxScale 21.06.17 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-210617-release-notes-2024-09-09.md)
* [MariaDB MaxScale 21.06.16 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-210616-release-notes-2024-06-03.md)
* [MariaDB MaxScale 6.4.15 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-6415-release-notes-2024-03-11.md)
* [MariaDB MaxScale 6.4.14 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-6414-release-notes-2024-02-09.md)
* [MariaDB MaxScale 6.4.13 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-6413-release-notes-2023-11-30.md)
* [MariaDB MaxScale 6.4.12 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-6412-release-notes-2023-11-03.md)
* [MariaDB MaxScale 6.4.11 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-6411-release-notes-2023-10-30.md)
* [MariaDB MaxScale 6.4.10 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-6410-release-notes-2023-08-30.md)
* [MariaDB MaxScale 6.4.9 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-649-release-notes-2023-08-21.md)
* [MariaDB MaxScale 6.4.8 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-648-release-notes-2023-07-31.md)
* [MariaDB MaxScale 6.4.7 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-647-release-notes-2023-05-24.md)
* [MariaDB MaxScale 6.4.6 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-646-release-notes-2023-03-29.md)
* [MariaDB MaxScale 6.4.5 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-645-release-notes-2023-01-13.md)
* [MariaDB MaxScale 6.4.4 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-644-release-notes-2022-11-29.md)
* [MariaDB MaxScale 6.4.3 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-643-release-notes-2022-10-14.md)
* [MariaDB MaxScale 6.4.2 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-642-release-notes-2022-09-02.md)
* [MariaDB MaxScale 6.4.1 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-641-release-notes-2022-07-14.md)
* [MariaDB MaxScale 6.4.0 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-640-release-notes-2022-06-09.md)

### MariaDB MaxScale 6.3

* Nosqlprotocol now supports both SSL and authentication.
* A large number of client connections can now share a smaller number of\
  backend connections.
* MaxGUI now shows which MaxScale node is in control when cooperative monitoring\
  is enabled.
* Filtering can now be used in the KafkaCDC router.
* The user is now informed if runtime changes are made to configuration objects\
  that are defined in static configuration files.

For more details, please refer to:

* [MariaDB MaxScale 6.3.1 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-631-release-notes-2022-05-16.md)
* [MariaDB MaxScale 6.3.0 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-630-release-notes-2022-04-14.md)

### MariaDB MaxScale 6.2

* Significant improvements and feature additions to MaxGUI
* Significant improvements to nosqlprotocol
* Transaction Performance Monitoring Filter functionality moved to Qlafilter
* Most filters can now be reconfigured at runtime
* Synchronous mode for the Tee filter
* New `list queries` command for MaxCtrl that lists all active queries
* MaxScale can read client user accounts from a file and map them to backend\
  users. See service setting [user\_accounts\_file](mariadb-maxscale-21-06-getting-started/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-configuration-guide.md)\
  and listener setting [user\_mapping\_file](mariadb-maxscale-21-06-getting-started/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-configuration-guide.md)\
  for more information.

For more details, please refer to:

* [MariaDB MaxScale 6.2.4 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-624-release-notes-2022-03-30.md)
* [MariaDB MaxScale 6.2.3 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-623-release-notes-2022-03-09.md)
* [MariaDB MaxScale 6.2.2 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-622-release-notes-2022-02-14.md)
* [MariaDB MaxScale 6.2.1 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-621-release-notes-2022-01-13.md)
* [MariaDB MaxScale 6.2.0 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-620-release-notes-2021-11-26.md)

### MariaDB MaxScale 6.1

* The versioning scheme has changed; earlier this would have been version 2.6.
* A `nosqlprotocol` protocol module that implements the MongoDB® wire protocol\
  has been introduced.
* The Columnstore monitor is now exclusively intended for Columnstore version 1.5.
* The Columnstore monitor can now automatically adapt to changes in the cluster\
  configuration.
* The Database Firewall filter has been deprecated.
* If extra\_port is defined for a server, it's used by default for monitor and\
  user account manager connections. Normal port is used if the extra-port\
  connection fails due to too low extra\_max\_connections-setting on the backend.
* The deprecated `required` and `disabled` values for the `ssl` parameter have been removed.
* Backend connection multiplexing added. See [idle\_session\_pool\_time](mariadb-maxscale-21-06-getting-started/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-configuration-guide.md)\
  for more information.
* Defaults for `maxctrl` can now be specified in the file `~/maxctrl.cnf`
* PAM Authenticator can map PAM users to MariaDB users.
* MariaDB-Monitor can launch monitor script when slave server exceeds replication\
  lag limit (`script_max_replication_lag`).
* MariaDB-Monitor can disable read\_only on master server\
  (`enforce_writable_master`).
* A graphical user interface SQL queries tool for writing, running SQL queries and visualizing\
  the results has been introduced.

For more details, please refer to:

* [MariaDB MaxScale 6.1.4 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-614-release-notes-2021-10-18.md)
* [MariaDB MaxScale 6.1.3 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-613-release-notes-20211001.md)
* [MariaDB MaxScale 6.1.2 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-612-release-notes-2021-09-27.md)
* [MariaDB MaxScale 6.1.1 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-611-release-notes.md)
* [MariaDB MaxScale 6.1.0 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-610-release-notes-2021-07-15.md)
* [MariaDB MaxScale 6.0.0 Release Notes](mariadb-maxscale-21-06-release-notes/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-600-release-notes-2021-06-30.md)

### MariaDB MaxScale 2.5

* MaxAdmin has been removed.
* MaxGUI, a new browser based tool for configuring and managing\
  MaxScale is introduced.
* MaxInfo-router and the related httpd-protocol have been removed.
* Server weights have been removed.
* Services can now directly route to other services with the help of the [target](mariadb-maxscale-21-06-getting-started/mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-configuration-guide.md) parameter.
* Server parameters protocol and authenticator have been deprecated. Any\
  definitions are ignored.
* Listeners support multiple authenticators.
* The replication lag of a slave server must now be less than [max\_slave\_replication\_lag](mariadb-maxscale-21-06-routers/mariadb-maxscale-2106-maxscale-2106-readwritesplit.md)\
  whereas in older versions the replication lag had to be less than or\
  equal to the configured limit.
* The global settings auth\_read\_timeout and auth\_write\_timeout have been\
  deprecated. Any definitions are ignored.
* The Columnstore monitor is now capable of monitoring Columnstore 1.5 in\
  addition to 1.0 and 1.2.
* MariaDB-Monitor supports cooperative monitoring. See [cooperative monitoring](mariadb-maxscale-2106-maxscale-21-06-monitors/mariadb-maxscale-2106-maxscale-2106-mariadb-monitor.md)\
  for more information.
* The MaxScale cache can now be shared between two MaxScale instances,\
  in which case either memcached or Redis can be used as cache storage.\
  Further, the cache can now also perform table level invalidations\
  and be specific to a particular user.
* A completely new binlog router implemenation.
* New routers, [mirror](mariadb-maxscale-21-06-routers/mariadb-maxscale-2106-maxscale-2106-mirror.md) and [kafkacdc](mariadb-maxscale-21-06-routers/mariadb-maxscale-2106-maxscale-2106-kafkacdc.md).
* Service-to-service routing is now possible with the `targets` parameter.
* TLS CRL and peer host verification support.
* Multiple modes of operation for `causal_reads`.

For more details, please refer to:

* [MariaDB MaxScale 2.5.29 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.29-Release-Notes.md)
* [MariaDB MaxScale 2.5.28 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.28-Release-Notes.md)
* [MariaDB MaxScale 2.5.27 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.27-Release-Notes.md)
* [MariaDB MaxScale 2.5.26 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.26-Release-Notes.md)
* [MariaDB MaxScale 2.5.25 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.25-Release-Notes.md)
* [MariaDB MaxScale 2.5.24 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.24-Release-Notes.md)
* [MariaDB MaxScale 2.5.23 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.23-Release-Notes.md)
* [MariaDB MaxScale 2.5.22 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.22-Release-Notes.md)
* [MariaDB MaxScale 2.5.21 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.21-Release-Notes.md)
* [MariaDB MaxScale 2.5.20 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.20-Release-Notes.md)
* [MariaDB MaxScale 2.5.19 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.19-Release-Notes.md)
* [MariaDB MaxScale 2.5.18 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.18-Release-Notes.md)
* [MariaDB MaxScale 2.5.17 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.17-Release-Notes.md)
* [MariaDB MaxScale 2.5.16 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.16-Release-Notes.md)
* [MariaDB MaxScale 2.5.15 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.15-Release-Notes.md)
* [MariaDB MaxScale 2.5.14 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.14-Release-Notes.md)
* [MariaDB MaxScale 2.5.13 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.13-Release-Notes.md)
* [MariaDB MaxScale 2.5.12 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.12-Release-Notes.md)
* [MariaDB MaxScale 2.5.11 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.11-Release-Notes.md)
* [MariaDB MaxScale 2.5.10 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.10-Release-Notes.md)
* [MariaDB MaxScale 2.5.9 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.9-Release-Notes.md)
* [MariaDB MaxScale 2.5.8 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.8-Release-Notes.md)
* [MariaDB MaxScale 2.5.7 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.7-Release-Notes.md)
* [MariaDB MaxScale 2.5.6 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.6-Release-Notes.md)
* [MariaDB MaxScale 2.5.5 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.5-Release-Notes.md)
* [MariaDB MaxScale 2.5.4 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.4-Release-Notes.md)
* [MariaDB MaxScale 2.5.3 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.3-Release-Notes.md)
* [MariaDB MaxScale 2.5.2 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.2-Release-Notes.md)
* [MariaDB MaxScale 2.5.1 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.1-Release-Notes.md)
* [MariaDB MaxScale 2.5.0 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.5.0-Release-Notes.md)

### MariaDB MaxScale 2.4

* A Clustrix specific monitor has been added.
* A new router, Smart Router, capable of routing a query to different\
  backends depending on the characteristics of the query has been added.
* Transaction replaying is now performed also in conjunction with server\
  initiated transaction rollbacks.
* Names starting with `@@` are reserved for use by MaxScale.
* Names can no longer contain whitespace.
* Servers can now be drained.
* The servers of a service can now be defined using a monitor.
* Durations can now be specified as hours, minutes, seconds or milliseconds.
* MaxCtrl commands `list sessions`, `show sessions` and `show session <id>`\
  support reverse DNS lookup of client addresses. The conversion is activated\
  by adding the `--rdns`-option to the command.
* The following MariaDB-Monitor settings have been removed and cause a startup error\
  if defined: `mysql51_replication`, `multimaster` and `allow_cluster_recovery`. The\
  setting `detect_replication_lag` is deprecated and ignored.
* `enforce_simple_topology`-setting added to MariaDB-Monitor.
* The mqfilter has been deprecated.

For more details, please refer to:

* [MariaDB MaxScale 2.4.19 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.19-Release-Notes.md)
* [MariaDB MaxScale 2.4.18 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.18-Release-Notes.md)
* [MariaDB MaxScale 2.4.17 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.17-Release-Notes.md)
* [MariaDB MaxScale 2.4.16 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.16-Release-Notes.md)
* [MariaDB MaxScale 2.4.15 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.15-Release-Notes.md)
* [MariaDB MaxScale 2.4.14 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.14-Release-Notes.md)
* [MariaDB MaxScale 2.4.13 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.13-Release-Notes.md)
* [MariaDB MaxScale 2.4.12 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.12-Release-Notes.md)
* [MariaDB MaxScale 2.4.11 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.11-Release-Notes.md)
* [MariaDB MaxScale 2.4.10 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.10-Release-Notes.md)
* [MariaDB MaxScale 2.4.9 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.9-Release-Notes.md)
* [MariaDB MaxScale 2.4.8 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.8-Release-Notes.md)
* [MariaDB MaxScale 2.4.7 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.7-Release-Notes.md)
* [MariaDB MaxScale 2.4.6 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.6-Release-Notes.md)
* [MariaDB MaxScale 2.4.5 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.5-Release-Notes.md)
* [MariaDB MaxScale 2.4.4 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.4-Release-Notes.md)
* [MariaDB MaxScale 2.4.3 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.3-Release-Notes.md)
* [MariaDB MaxScale 2.4.2 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.2-Release-Notes.md)
* [MariaDB MaxScale 2.4.1 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.1-Release-Notes.md)
* [MariaDB MaxScale 2.4.0 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.4.0-Release-Notes.md)

### MariaDB MaxScale 2.3

* Runtime Configuration of the Cache
* User Specified Syslog Facility and Level for Authentication Errors
* `config reload` removed from MaxAdmin (was deprecated in 2.2)
* MariaDBMonitor features added, modified and removed
* A Comment filter has been added.
* Services and filters can be created at runtime via the REST API
* Runtime router reconfiguration is now possible
* New Throttle filter that replaces and extends on the limit\_queries functionality
* MaxCtrl
* The `create monitor` command now accepts a list of key-value parameters
* The new `drain server` drains the server of connections
* A new interactive input mode was added
* Readwritesplit
* Automatic transaction replay allows transactions to be migrated between servers
* Master connections can now be re-opened
* Writes with autocommit enabled can be automatically retried
* Consistent reads on slaves via MASTER\_GTID\_WAIT
* Transaction load balancing for normal transactions
* Support for runtime router reconfiguration
* A new load balancing method: ADAPTIVE\_ROUTING
* Experimental resultset concatenation router, `cat`
* The schema router is now capable of table family sharding.
* The binlog router can now automatically switch to secondary masters\
  when replicating from a Galera cluster in case the primary master\
  goes down.
* MaxScale now has a systemd compatible watchdog.
* Server setting `authenticator_options` is no longer used and any value is\
  ignored.

For more details, please refer to:

* [MariaDB MaxScale 2.3.20 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.20-Release-Notes.md)
* [MariaDB MaxScale 2.3.19 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.19-Release-Notes.md)
* [MariaDB MaxScale 2.3.18 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.18-Release-Notes.md)
* [MariaDB MaxScale 2.3.17 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.17-Release-Notes.md)
* [MariaDB MaxScale 2.3.16 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.16-Release-Notes.md)
* [MariaDB MaxScale 2.3.15 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.15-Release-Notes.md)
* [MariaDB MaxScale 2.3.14 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.14-Release-Notes.md)
* [MariaDB MaxScale 2.3.13 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.13-Release-Notes.md)
* [MariaDB MaxScale 2.3.12 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.12-Release-Notes.md)
* [MariaDB MaxScale 2.3.11 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.11-Release-Notes.md)
* [MariaDB MaxScale 2.3.10 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.10-Release-Notes.md)
* [MariaDB MaxScale 2.3.9 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.9-Release-Notes.md)
* [MariaDB MaxScale 2.3.8 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.8-Release-Notes.md)
* [MariaDB MaxScale 2.3.7 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.7-Release-Notes.md)
* [MariaDB MaxScale 2.3.6 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.6-Release-Notes.md)
* [MariaDB MaxScale 2.3.5 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.5-Release-Notes.md)
* [MariaDB MaxScale 2.3.4 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.4-Release-Notes.md)
* [MariaDB MaxScale 2.3.3 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.3-Release-Notes.md)
* [MariaDB MaxScale 2.3.2 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.2-Release-Notes.md)
* [MariaDB MaxScale 2.3.1 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.1-Release-Notes.md)
* [MariaDB MaxScale 2.3.0 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.3.0-Release-Notes.md)

### MariaDB MaxScale 2.2

* Limited support from Pluggable Authentication Modules (PAM).
* Proxy protocol support for backend connections.
* REST-API for obtaining information about and for manipulating the\
  resources of MaxScale.
* MaxCtrl, a new command line client for administering MaxScale\
  implemented in terms of the REST-API.
* Firewall can now prevent the use of functions in conjunction with\
  certain columns.
* Parser of MaxScale extended to support window functions and CTEs.
* Parser of MaxScale extended to support PL/SQL compatibility features\
  of upcoming 10.3 release.
* Prepared statements are now parsed and the execution of read only\
  ones will be routed to slaves.
* Server states are persisted, so in case of crash and restart MaxScale\
  has the correct server state quicker.
* Monitor scripts are executed synchronously, so they can safely perform\
  actions that change the server states.
* The Masking filter can now both obfuscate and partially mask columns.
* Binlog router supports MariaDB 10 GTID at both ends.
* KILL CONNECTION can now be used through MaxScale.
* Environment variables can now be used in the MaxScale configuration file.
* By default, MaxScale can no longer be run as root.
* The MySQL Monitor is now capable of performing failover and switchover of\
  the master. There is also limited capability for rejoining nodes.

For more details, please refer to:

* [MariaDB MaxScale 2.2.21 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.21-Release-Notes.md)
* [MariaDB MaxScale 2.2.20 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.20-Release-Notes.md)
* [MariaDB MaxScale 2.2.19 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.19-Release-Notes.md)
* [MariaDB MaxScale 2.2.18 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.18-Release-Notes.md)
* [MariaDB MaxScale 2.2.17 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.17-Release-Notes.md)
* [MariaDB MaxScale 2.2.16 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.16-Release-Notes.md)
* [MariaDB MaxScale 2.2.15 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.15-Release-Notes.md)
* [MariaDB MaxScale 2.2.14 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.14-Release-Notes.md)
* [MariaDB MaxScale 2.2.13 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.13-Release-Notes.md)
* [MariaDB MaxScale 2.2.12 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.12-Release-Notes.md)
* [MariaDB MaxScale 2.2.11 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.11-Release-Notes.md)
* [MariaDB MaxScale 2.2.10 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.10-Release-Notes.md)
* [MariaDB MaxScale 2.2.9 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.9-Release-Notes.md)
* [MariaDB MaxScale 2.2.8 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.8-Release-Notes.md)
* [MariaDB MaxScale 2.2.7 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.7-Release-Notes.md)
* [MariaDB MaxScale 2.2.6 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.6-Release-Notes.md)
* [MariaDB MaxScale 2.2.5 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.5-Release-Notes.md)
* [MariaDB MaxScale 2.2.4 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.4-Release-Notes.md)
* [MariaDB MaxScale 2.2.3 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.3-Release-Notes.md)
* [MariaDB MaxScale 2.2.2 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.2-Release-Notes.md)
* [MariaDB MaxScale 2.2.1 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.1-Release-Notes.md)
* [MariaDB MaxScale 2.2.0 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.2.0-Release-Notes.md)

### MariaDB MaxScale 2.1

* MariaDB MaxScale is licensed under MariaDB BSL 1.1.
* Hierarchical configuration files are now supported.
* Logging is now performed in a way compatible with logrotate(8).
* Persistent connections are reset upon reuse.
* Galera monitor now consistently chooses the same node as master.
* Galera Monitor can set the preferred donor nodes list.
* The configuration can now be altered dynamically and the changes are persisted.
* There is now a monitor for Amazon Aurora clusters.
* MySQL Monitor now has a multi-master mode.
* MySQL Monitor now has a failover mode.
* Named Server Filter now supports wildcards for source option.
* Binlog Server can now be configured to encrypt binlog files.
* New filters, cache, ccrfilter, insertstream, masking, and maxrows are introduced.
* GSSAPI based authentication can be used
* Prepared statements are now in the database firewall filtered exactly like non-prepared\
  statements.
* The firewall filter can now filter based on function usage.
* MaxScale now supports IPv6

For more details, please refer to:

* [MariaDB MaxScale 2.1.17 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.17-Release-Notes.md)
* [MariaDB MaxScale 2.1.16 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.16-Release-Notes.md)
* [MariaDB MaxScale 2.1.15 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.15-Release-Notes.md)
* [MariaDB MaxScale 2.1.14 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.14-Release-Notes.md)
* [MariaDB MaxScale 2.1.13 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.13-Release-Notes.md)
* [MariaDB MaxScale 2.1.12 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.12-Release-Notes.md)
* [MariaDB MaxScale 2.1.11 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.11-Release-Notes.md)
* [MariaDB MaxScale 2.1.10 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.10-Release-Notes.md)
* [MariaDB MaxScale 2.1.9 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.9-Release-Notes.md)
* [MariaDB MaxScale 2.1.8 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.8-Release-Notes.md)
* [MariaDB MaxScale 2.1.7 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.7-Release-Notes.md)
* [MariaDB MaxScale 2.1.6 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.6-Release-Notes.md)
* [MariaDB MaxScale 2.1.5 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.5-Release-Notes.md)
* [MariaDB MaxScale 2.1.4 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.4-Release-Notes.md)
* [MariaDB MaxScale 2.1.3 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.3-Release-Notes.md)
* [MariaDB MaxScale 2.1.2 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.2-Release-Notes.md)
* [MariaDB MaxScale 2.1.1 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.1-Release-Notes.md)
* [MariaDB MaxScale 2.1.0 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.1.0-Release-Notes.md)

### MariaDB MaxScale 2.0

* MariaDB MaxScale is licensed under MariaDB BSL.
* SSL can be used in the communication between MariaDB MaxScale and the backend servers.
* The number of allowed connections can explicitly be throttled.
* MariaDB MaxScale can continue serving read request even if the master has gone down.
* The security of MaxAdmin has been improved; Unix domain sockets can be used in the\
  communication with MariaDB MaxScale and the Linux identity can be used for authorization.
* MariaDB MaxScale can in real time make binlog events available as raw AVRO or\
  as JSON objects (beta level functionality).

For more details, please refer to:

* [MariaDB MaxScale 2.0.6 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.0.6-Release-Notes.md)
* [MariaDB MaxScale 2.0.5 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.0.5-Release-Notes.md)
* [MariaDB MaxScale 2.0.4 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.0.4-Release-Notes.md)
* [MariaDB MaxScale 2.0.3 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.0.3-Release-Notes.md)
* [MariaDB MaxScale 2.0.2 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.0.2-Release-Notes.md)
* [MariaDB MaxScale 2.0.1 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.0.1-Release-Notes.md)
* [MariaDB MaxScale 2.0.0 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-2.0.0-Release-Notes.md)

### MariaDB MaxScale 1.4

* Authentication now allows table level resolution of grants. MaxScale service\
  users will now need SELECT privileges on `mysql.tables_priv` to be able to\
  authenticate users at the database and table level.
* Firewall filter allows whitelisting.
* Client side SSL works.

For more details, please refer to [_MariaDB MaxScale 1.4.3 Release Notes_](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-1.4.3-Release-Notes.md) [MariaDB MaxScale 1.4.2 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-1.4.2-Release-Notes.md)[_MariaDB MaxScale 1.4.1 Release Notes_](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-1.4.1-Release-Notes.md) [MariaDB MaxScale 1.4.0 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-1.4.0-Release-Notes.md).

### MariaDB MaxScale 1.3

* Added support for persistent backend connections
* The binlog server is now an integral component of MariaDB MaxScale.
* The logging has been changed; instead of different log files there is one log file and different message priorities.

For more details, please refer to [MariaDB MaxScale 1.3 Release Notes](https://github.com/mariadb-corporation/docs-server/blob/test/maxscale/mariadb-maxscale-21-06/Release-Notes/MaxScale-1.3.0-Release-Notes.md)

### MariaDB MaxScale 1.2

* Logfiles have been renamed. The log names are now named error.log, messages.log, trace.log and debug.log.

### MariaDB MaxScale 1.1.1

* Schemarouter now also allows for an upper limit to session commands.
* Schemarouter correctly handles SHOW DATABASES responses that span multiple buffers.
* Readwritesplit and Schemarouter now allow disabling of the session command history.

### MariaDB MaxScale 1.1

**NOTE:** MariaDB MaxScale default installation directory has changed to `/usr/local/mariadb-maxscale` and the default password for MaxAdmin is now ´mariadb´.

* New modules added
  * Binlog router
  * Firewall filter
  * Multi-Master monitor
  * RabbitMQ logging filter
  * Schema Sharding router
* Added option to use high precision timestamps in logging.
* Readwritesplit router now returns the master server's response.
* New readwritesplit router option added. It is now possible to control the amount of memory readwritesplit sessions will consume by limiting the amount of session modifying statements they can execute.
* Minimum required CMake version is now 2.8.12 for package building.
* Session idle timeout added for services. More details can be found in the configuration guide.
* Monitor API is updated to 2.0.0. Monitors with earlier versions of the API no longer work with this version of MariaDB MaxScale.
* MariaDB MaxScale now requires libcurl and libcurl development headers.
* Nagios plugins added.
* Notification service added.
* Readconnrouter has a new "running" router\_option. This allows it to use any running server as a valid backend server.
* Database names can be stripped of escape characters with the `strip_db_esc` service parameter.

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
