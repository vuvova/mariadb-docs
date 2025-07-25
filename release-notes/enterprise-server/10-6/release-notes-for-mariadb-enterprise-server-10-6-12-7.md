# Release Notes for MariaDB Enterprise Server 10.6.12-7

MariaDB Enterprise Server 10.6.12-7 is a maintenance release of [MariaDB Enterprise Server](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/mariadb-enterprise-server/README.md) 10.6. This release includes a variety of fixes.

MariaDB Enterprise Server 10.6.12-7 was released on 2023-03-13.

Users of MariaDB Enterprise Server 10.6.12-7 are encouraged to upgrade to 10.6.12-8. Please see the [special upgrade procedure](release-notes-for-mariadb-enterprise-server-10-6-12-8.md#upgrade-procedure) that must be used.

### Backported Features

MariaDB Enterprise Server enables a predictable development and operations experience through an [enterprise lifecycle](../enterprise-server-lifecycle.md). These new features have been backported after reaching maturity in MariaDB Community Server.

* In previous releases, the number of undo logs was configurable before InnoDB was initialized. With this release, the number of undo logs can also be configured after install.
  * The number of undo logs is configured by the InnoDB system variable `--innodb-undo-tablespaces`.
  * Splitting undo logs over multiple tablespaces can reduce the size of a single tablespace, especially the InnoDB system tablespace.
  * In previous releases, the number of undo logs had to be configured before InnoDB was initialized, so changing the number of undo logs would require setting up a new server instance. With this backport from MariaDB Community Server 10.11, the number of undo logs can be changed so it will take effect with the next server start. (MENT-1650)

### Notable Changes

* Output for the [JSON\_DETAILED()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_detailed) function has been optimized to reduce the number of lines needed. ([MDEV-19160](https://jira.mariadb.org/browse/MDEV-19160))
  * For compatibility, [JSON\_PRETTY()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_pretty) has been added as an alias to JSON\_DETAILED(). ([MDEV-19160](https://jira.mariadb.org/browse/MDEV-19160))
* This release incorporates Galera library version 26.4.14.
* The names used by `information_schema.INNODB_TABLESPACES_ENCRYPTION.NAME` for undo tablespaces have been changed. ([MDEV-30119](https://jira.mariadb.org/browse/MDEV-30119))\
  Starting with this release, names for the undo tablespaces use the format undo001.\
  In previous releases, names for the undo tablespaces used `NULL`.
* For MariaDB Enterprise Cluster SST with `MariaDB Enterprise Backup` backup execution (namely the block DDL phase) has been changed. In previous releases, the node was paused from the cluster, generating the following log file entry: ([MDEV-26391](https://jira.mariadb.org/browse/MDEV-26391))

```
WSREP: Shifting SYNCED -> DONOR/DESYNCED
```

* Starting with this release, the mariadb-backup execution can be aborted if DDL statements happen during backup execution. This abortable backup execution is the optional feature which can be enabled/disabled by `wsrep_mode: BF_ABORT_mariadb-backup`

### Issues Fixed

#### Can result in data loss

* When executing a `DELETE` or `UPDATE` with a subselect, the server can crash. ([MDEV-10087](https://jira.mariadb.org/browse/MDEV-10087))
* When performing an incremental backup, MariaDB Enterprise Backup does not reflect databases that have been dropped and created. ([MDEV-23335](https://jira.mariadb.org/browse/MDEV-23335))
* During recovery, MariaDB Server can crash with an error when a DDL operation was executed before the server was stopped: `InnoDB: Trying to write ... bytes at ... outside the bounds of the file ...` ([MDEV-30069](https://jira.mariadb.org/browse/MDEV-30069))
* `innodb_undo_log_truncate=ON` is not crash safe. This also can have effects for MariaDB Enterprise Backup for backup and restore. ([MDEV-29999](https://jira.mariadb.org/browse/MDEV-29999), [MDEV-30179](https://jira.mariadb.org/browse/MDEV-30179), [MDEV-30438](https://jira.mariadb.org/browse/MDEV-30438))
  * When `innodb_undo_log_truncate=ON` a backup for MariaDB Enterprise Server can return the error message:

```
FATAL ERROR: ... failed to copy datafile.
```

#### Can result in a hang or crash

* When `DELETE HISTORY` is executed for a system versioned table with full text index, the server can crash. ([MDEV-25004](https://jira.mariadb.org/browse/MDEV-25004))
* When an `ALTER TABLE` statement causes InnoDB to rebuild a table with a spatial index, the server can crash. ([MDEV-29856](https://jira.mariadb.org/browse/MDEV-29856))
* When using SPIDER with `SPIDER_DIRECT_SQL` and `spider_udf_ds_use_real_table=1`, the server can crash. ([MDEV-29855](https://jira.mariadb.org/browse/MDEV-29855))
* When executing `REPLACE INTO ... PARTITION(...)`, the server can crash. ([MDEV-29636](https://jira.mariadb.org/browse/MDEV-29636))
* `Galera SST` doesn't properly handle undo\* files from InnoDB. As a result, SST may terminate incorrectly when `--innodb-undo-tablespaces` is set to 3 or more. ([MDEV-30157](https://jira.mariadb.org/browse/MDEV-30157))
* With a query containing nested `WINDOW` clauses, the server can crash. ([MDEV-30052](https://jira.mariadb.org/browse/MDEV-30052))
* When executing a `SELECT` from complex a view with `WHERE` clause and with the setting `derived_merge=on`, the server can crash. ([MDEV-30081](https://jira.mariadb.org/browse/MDEV-30081))
* Infinite sequence of recursive calls when processing embedded CTE, when such a reference has the same table name as the name of the `CTE`. ([MDEV-30248](https://jira.mariadb.org/browse/MDEV-30248))
* With a cluster wide conflict, MariaDB Enterprise Cluster can hang if a `binlog` purging is running (such as in the case that, binlog expiration is configured). ([MDEV-29512](https://jira.mariadb.org/browse/MDEV-29512))
* `mariadbd` hangs when running with `--wsrep-recover` and `--plugin-load-add=ha_spider.so` options. ([MDEV-30370](https://jira.mariadb.org/browse/MDEV-30370))
* After a second execution via a stored routine or a prepared statement of a `LEAD ... OVER` query, the server can crash. ([MDEV-28206](https://jira.mariadb.org/browse/MDEV-28206))
* When `innodb_undo_log_truncate=ON` is set, the server can hang. ([MDEV-30180](https://jira.mariadb.org/browse/MDEV-30180))
* After recovery, the server can crash with an error if `innodb_buffer_pool_size` is not large enough to recover in a single batch: `InnoDB: Tried to read ... bytes at offset` ([MDEV-30132](https://jira.mariadb.org/browse/MDEV-30132))
* Race condition in foreign key locking during truncate. ([MDEV-29504](https://jira.mariadb.org/browse/MDEV-29504))
* Possible hangs in some `B-tree` operations. ([MDEV-30400](https://jira.mariadb.org/browse/MDEV-30400), [MDEV-29603](https://jira.mariadb.org/browse/MDEV-29603))
* MariaDB Enterprise Backup can hang when using the parameters `--backup --incremental --throttle=...` ([MDEV-29896](https://jira.mariadb.org/browse/MDEV-29896))
* While executing an `ALTER TABLE` for a compressed `InnoDB` table, the server can crash. ([MDEV-28797](https://jira.mariadb.org/browse/MDEV-28797))
* InnoDB fails to remove a newly created table or index from data dictionary and table cache and then crashes, if the `ALTER` to add a `FULLTEXT` index fails in the commit phase. ([MDEV-30393](https://jira.mariadb.org/browse/MDEV-30393))
* When the query cache is enabled and a `DROP DATABASE` is called, the `DROP DATABASE` can hang and 100 percent CPU load can be seen. ([MDEV-29760](https://jira.mariadb.org/browse/MDEV-29760))
* The execution of `FLUSH TABLES...FOR EXPORT` can result in a server crash. ([MDEV-30227](https://jira.mariadb.org/browse/MDEV-30227))
* When querying a Spider table from a stored procedure inside a `WHILE` clause, the server can crash. The stored procedure needs to use two `WHILE` clauses which both query the Spider table. ([MDEV-30191](https://jira.mariadb.org/browse/MDEV-30191))
* Deadlock on `Replica` during `BACKUP STAGE BLOCK_COMMIT on XA` transactions. ([MDEV-30423](https://jira.mariadb.org/browse/MDEV-30423))
* MariaDB Server can crash during recovery if an `ALTER TABLE .. ROW_FORMAT=COMPRESSED` has been executed before. ([MDEV-30404](https://jira.mariadb.org/browse/MDEV-30404))

#### Can result in unexpected behavior

* `log_query_not_using_indexes=OFF` is ignored when `log_slow_filter` is an empty string. ([MDEV-21187](https://jira.mariadb.org/browse/MDEV-21187))
* MariaDB Enterprise Backup returns with an error when the option `--galera-info` is used for creating a backup of a MariaDB Server instance, which is not a MariaDB Enterprise Cluster node. `Failed to get master wsrep state from SHOW STATUS` ([MDEV-30293](https://jira.mariadb.org/browse/MDEV-30293))
* When querying a table with virtual generated columns using full text search, these columns are not generated and are always `NULL` in the result set. ([MDEV-29169](https://jira.mariadb.org/browse/MDEV-29169))
* Identifiers are not quoted for the output of `SHOW GRANTS`. Using the result to execute the grant statement results in a syntax error, if reserved keywords are used. ([MDEV-30056](https://jira.mariadb.org/browse/MDEV-30056))
* Spider table with CHARSET `utf32/utf16/ucs2` tries to set client CHARSET to unsupported value. ([MDEV-29562](https://jira.mariadb.org/browse/MDEV-29562))
* Incorrect results are returned when using `STDDEV_SAMP()` with a view. ([MDEV-19071](https://jira.mariadb.org/browse/MDEV-19071))
* A spurious error can be generated: `ERROR 1292 (22007) at the line 15: Truncated incorrect DECIMAL value:`

## ([MDEV-30342](https://jira.mariadb.org/browse/MDEV-30342))

* When running `mariadb-binlog` using the option --verbose, cannot read row events with compressed columns: `Error: Don't know how to handle column type:...` ([MDEV-25277](https://jira.mariadb.org/browse/MDEV-25277))
* Incorrect results are returned with outer join, merged derived table, and view. ([MDEV-28602](https://jira.mariadb.org/browse/MDEV-28602))
* Some DDL, such as `ANALYZE`, can be completed out of order on parallel replicas. ([MDEV-30323](https://jira.mariadb.org/browse/MDEV-30323))
* `seconds_behind_master` is incorrect for delayed parallel replicas. ([MDEV-29639](https://jira.mariadb.org/browse/MDEV-29639))
* Unlimited SELECT .. ORDER BY .. LIMIT can be slow as it is always using temporary. ([MDEV-29129](https://jira.mariadb.org/browse/MDEV-29129))
* Calling `DETERMINISTIC` package functions from other SQL/PL stored routines can be slow. ([MDEV-29370](https://jira.mariadb.org/browse/MDEV-29370))
* An upgrade to MariaDB Server 10.5 and [MariaDB 10.6](../../community-server/mariadb-10-6-series/what-is-mariadb-106.md) incorrectly reports that a recovery is needed. ([MDEV-24412](https://jira.mariadb.org/browse/MDEV-24412))
* Warning message when encryption is not available on recovery: `InnoDB: We do not continue the crash recovery, because the table may become corrupt` ([MDEV-30068](https://jira.mariadb.org/browse/MDEV-30068))
* With MariaDB Enterprise Backup on Windows, an incremental prepare fails when `innodb_undo_tablespaces > 0` is set. ([MDEV-30144](https://jira.mariadb.org/browse/MDEV-30144))
* Changing the value of wsrep\_gtid\_domain\_id for MariaDB Enterprise Cluster with full cluster restart can fail on nodes, which do not sync from the node where `wsrep_gtid_domain_id` was changed. ([MDEV-29171](https://jira.mariadb.org/browse/MDEV-29171))

### Changes in Storage Engines

* This release originally incorporated MariaDB ColumnStore storage engine version 23.02.1.
* This release later incorporated MariaDB ColumnStore storage engine version 23.02.2.
* This release now incorporates MariaDB ColumnStore storage engine version 23.02.3.

### Interface Changes

* Error code `5016` added.
* [columnstore\_group\_by\_handler](https://app.gitbook.com/s/rBEU9juWLfTDcdwF3Q14/management/columnstore-system-variables) system variable default value changed from `ON` to `OFF`
* [JSON\_PRETTY()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_pretty) function added.

### Platforms

In alignment to the [enterprise lifecycle](../enterprise-server-lifecycle.md), MariaDB Enterprise Server 10.6.12-7 is provided for:

* CentOS 7 (x86\_64)
* Debian 10 (x86\_64, ARM64)
* Debian 11 (x86\_64, ARM64)
* Microsoft Windows (x86\_64) (MariaDB Enterprise Cluster excluded)
* Red Hat Enterprise Linux 7 (x86\_64)
* Red Hat Enterprise Linux 8 (x86\_64, ARM64)
* Red Hat Enterprise Linux 9 (x86\_64, ARM64)
* Rocky Linux 8 (x86\_64, ARM64)
* Rocky Linux 9 (x86\_64, ARM64)
* SUSE Linux Enterprise Server 12 (x86\_64)
* SUSE Linux Enterprise Server 15 (x86\_64, ARM64)
* Ubuntu 18.04 (x86\_64, ARM64)
* Ubuntu 20.04 (x86\_64, ARM64)
* Ubuntu 22.04 (x86\_64, ARM64)

Some components of MariaDB Enterprise Server might not support all platforms. For additional information, see [MariaDB Corporation Engineering Policies".](https://mariadb.com/engineering-policies)

### Installation Instructions

* [MariaDB Enterprise Server ](../11-4/whats-new-in-mariadb-enterprise-server-11-4.md)[10](broken-reference)[.6](../11-4/whats-new-in-mariadb-enterprise-server-11-4.md)
* [Enterprise Cluster Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[10](broken-reference)[.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Primary/Replica Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/primary-replica)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/primary-replica)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [ColumnStore Object Storage Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)
* [ColumnStore Shared Local Storage Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)
* [HTAP Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)
* [Single-Node Enterprise ColumnStore 23.02 with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and Object Storage](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)
* [Single-Node Enterprise ColumnStore 23.02 with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Enterprise Spider Sharded Topology with MariaDB Enterprise Server ](broken-reference)[10](broken-reference)[.](broken-reference)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Enterprise Spider Federated Topology with MariaDB Enterprise Server 10.](broken-reference)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)

## Upgrade Instructions

* [Upgrade to MariaDB Enterprise Server 10.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/install-and-upgrade-mariadb/upgrading/upgrading-from-to-specific-versions/upgrading-from-mariadb-10-5-to-mariadb-10-6)
* [Upgrade from MariaDB Community Server to MariaDB Enterprise Server 10.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/install-and-upgrade-mariadb/upgrading/upgrading-between-major-mariadb-versions)

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
