# Release Notes for MariaDB Enterprise Server 10.6.17-12

MariaDB Enterprise Server 10.6.17-12 is a maintenance release of [MariaDB Enterprise Server](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/mariadb-enterprise-server/README.md) 10.6. This release includes a variety of fixes.

MariaDB Enterprise Server 10.6.17-12 was released on 2024-03-11.

#### Note

MariaDB Enterprise Server 10.6.17-12 introduced a regression which can result in a server crash. Users are encouraged to update to MariaDB Enterprise Server 10.6.17-13. If an update not possible we recommend to increase your current setting for `--thread_stack` by 100k.\
Please see the Release Notes for [MariaDB Enterprise Server 10.6.17-13](release-notes-for-mariadb-enterprise-server-10-6-17-13.md) for details.

## Changes in Storage Engines

* This release incorporates MariaDB ColumnStore engine version 23.10.1.

## Notable Changes

* Galera has been updated to 26.4.17
* AlmaLinux 8 and 9 are now officially supported. RHEL 8 and 9 packages are used for AlmaLinux
* Deprecation of `secure_auth=0` with this release ([MDEV-32617](https://jira.mariadb.org/browse/MDEV-32617))
* New variable `optimizer_adjust_secondary_key_costs` ([MDEV-33118](https://jira.mariadb.org/browse/MDEV-33118))
  * This variable changes the optimizer behavior in the case where the optimizer wrongly uses a secondary key instead of a clustered primary key for InnoDB.
  * The different values for the new variable:
    * `optimizer_adjust_secondary_key_costs=0` (default)
      * No changes to current model
    * `optimizer_adjust_secondary_key_costs=1`
      * Ensures that the cost of secondary indexes has a cost of at least 5x times the cost of a primary key
    * `optimizer_adjust_secondary_key_costs=2`
      * Disable `worst_seek` optimization and slightly adjust filter cost (add cost of 1 if filter is used)
* Users with `ALL PRIVILEGES` on a db will now also see all routine bodies in that db (MENT-1983)
* More detailed logging for network related errors has been added. Use `--log-warnings=4` or higher to enable it. (MENT-2054)
* Thread ID and database are now added to the log of the SQL error plugin, if `sql_error_log_with_db_and_thread_info=ON` is set : ([MDEV-27087](https://jira.mariadb.org/browse/MDEV-27087))

## Issues Fixed

### Can result in data loss

* `BLOB` corruption on `UPDATE of PRIMARY KEY` with `FOREIGN KEY` ([MDEV-31441](https://jira.mariadb.org/browse/MDEV-31441))
* Corrupted table after instant `ADD COLUMN` failed due to attempting to exceed the maximum record length ([MDEV-18322](https://jira.mariadb.org/browse/MDEV-18322))
* If tables are frequently created, renamed, dropped, a backup cannot be restored. mariadb-backup --prepare might fail or finish OK, but some data files of recently created tables would be corrupted ([MDEV-32939](https://jira.mariadb.org/browse/MDEV-32939))
* ALTER command, before entering TOI, tries to collect foreign keys of a table. For this it opens the main table with SHARED\_HIGH\_PRIO MDL lock which disregards any waiting queued lock requests. If there is a DML operation running on the same table, and a real TOI operation as well, this TOI operation tries to BF-abort DML operation. At the same time, because ALTER is not yet TOI, and it runs with HIGH\_PRIO MDL lock, it disregards waiting TOI operation, and gets the lock and immediately gets BF-aborted either by TOI directly or by aborted DML operation. Since there is no wsrep transaction for ALTER, it gets BF-aborted by setting killed state for the tread. But before entering TOI, ALTER doesn't check killed state, so it replicates, and applies on the other nodes successfully, but then it rolls back on the local node, causing inconsistency ([MDEV-32938](https://jira.mariadb.org/browse/MDEV-32938))
* If Galera is enabled with binlog emulation, attempting to set a `SAVEPOINT` when one of the involved storage engines does not support savepoints, can result in cluster wide inconsistency. A part of a transaction could be replicated to other notes, but a local statement rollback could be triggered. ([MDEV-32549](https://jira.mariadb.org/browse/MDEV-32549))
* InnoDB after issuing `ALTER TABLE...IMPORT TABLESPACE` may not be crash safe anymore ([MDEV-32269](https://jira.mariadb.org/browse/MDEV-32269))
* When a table is created with a virtual column while using `sql_mode=ORACLE`, the server can crash when the table is changed while using a different setting for `sql_mode` ([MDEV-27744](https://jira.mariadb.org/browse/MDEV-27744))
  * The virtual column must have been created using:
    * `DECODE()`
    * `LTRIM()`
    * `RTRIM()`
    * `LPAD()`
    * `RPAD()`
    * `REPLACE()`
    * `SUBSTR()`

### Can result in hang or crash

* Possible deadlock when accessing BLOBs in a corrupted InnoDB table with `ROW_FORMAT=COMPRESSED` ([MDEV-32371](https://jira.mariadb.org/browse/MDEV-32371))
* An `INSERT .. FROM SELECT` with an empty result set crashes with `innodb_force_recovery=6` or `innodb_read_only=ON` ([MDEV-31861](https://jira.mariadb.org/browse/MDEV-31861))
* A shutdown of the server with `innodb_fast_shutdown=0` can hang after the server failed to start up ([MDEV-32798](https://jira.mariadb.org/browse/MDEV-32798))
* Crash while trying to complain "unsupported meta-data version" on `ALTER TABLE...IMPORT TABLESPACE` with MySQL 8.0 files ([MDEV-29972](https://jira.mariadb.org/browse/MDEV-29972))
* Wrong table attribute `PAGE_COMPRESSED=1` shown for tables in the InnoDB system tablespace ([MDEV-31000](https://jira.mariadb.org/browse/MDEV-31000))
* MariaDB crashes with foreign\_key\_checks=0 when changing a column and adding a foreign key at the same time ([MDEV-32638](https://jira.mariadb.org/browse/MDEV-32638))
* Sometimes node has been dropped from the cluster on startup `Shutdown with async replica` ([MDEV-31413](https://jira.mariadb.org/browse/MDEV-31413)) with diagnostics like:

```
[ERROR] Slave SQL: Error 'WSREP has not yet prepared node for application use' on query
```

and

```
[ERROR] Slave SQL: Node has dropped from cluster, Gtid 1-1-1, Internal MariaDB error code: 1047" in the server log
```

* `GTIDs` may diverge in Galera cluster after `CREATE TABLE AS` ([MDEV-27806](https://jira.mariadb.org/browse/MDEV-27806))\
  This can subsequently lead to diagnostics like:

```
[ERROR] mariadbd: Error writing file '/opt/maria10.1/binlog/BINLOG' (errno: 1950 "Unknown error 1950")"
```

and node crash:

```
wsrep::transaction::before_rollback(): Assertion state() == s_executing || state() == s_preparing || state() == s_prepared || state() == s_must_abort || state() == s_aborting || state() == s_cert_failed || state() == s_must_replay` failed
```

* `SHOW SLAVE STATUS` can deadlock an errored replica when a parallel replica worker gets killed at about when SHOW is issued ([MDEV-10653](https://jira.mariadb.org/browse/MDEV-10653))
* When executing `SELECT BINLOG_GTID_POS(@binlog_file...)` with the user variable being NULL, the server can crash ([MDEV-33045](https://jira.mariadb.org/browse/MDEV-33045))
* A Query that uses a specific SQL construct can cause a server crash. The construct is an equality comparison of table-less row subquery and a subquery that has a UNION operation at the top level: (`SELECT 'foo', 'bar') = (SELECT col1, col2 FROM t1 ... UNION ...)` ([MDEV-29070](https://jira.mariadb.org/browse/MDEV-29070))
* A `DELETE` with `ORDER BY` and semijoin optimization can cause a crash ([MDEV-32212](https://jira.mariadb.org/browse/MDEV-32212))
* Possible crash when lateral derived in a query is guaranteed to return no rows ([MDEV-31279](https://jira.mariadb.org/browse/MDEV-31279))
* When using `EXCHANGE PARTITION` to replace a partition with a table, the server can crash if the to be exchanged table is using a virtual column which is not matching the partitioning key ([MDEV-28127](https://jira.mariadb.org/browse/MDEV-28127))
* When using `INSERT DELAYED` with a table using virtual columns, the server can crash ([MDEV-29932](https://jira.mariadb.org/browse/MDEV-29932))
* When using `SELECT` from a derived table with using AS OF, the server can crash ([MDEV-32082](https://jira.mariadb.org/browse/MDEV-32082))
* When using `JSON_CONTAINS_PATH` in a comparison in a prepared statement, the server can crash on execution of the statement ([MDEV-32867](https://jira.mariadb.org/browse/MDEV-32867))
* `mariadbd --bootstrap / mariadb_install_db` hangs when Spider is installed ([MDEV-32903](https://jira.mariadb.org/browse/MDEV-32903))
* Binlog Checksum of replication user variable events is zeroed by Zlib if part of event data is empty. The bug is a regression of other fixes on a server build with the zlib library. It can show up as a checksum verification error of a user variable event at its reading from binlog, ([MDEV-33283](https://jira.mariadb.org/browse/MDEV-33283))
* When adding a second semi-sync replica to a primary, it can hang at connect time without receiving any events, until the primary receives an ACK from the first existing replica. This can be indefinite if no new transactions occur on the primary ([MDEV-32792](https://jira.mariadb.org/browse/MDEV-32792))
* Server hangs on `DROP DATABASE` after a failing `LOCK TABLES` on Spider table ([MDEV-29667](https://jira.mariadb.org/browse/MDEV-29667))
* When a prepared statement with subqueries and window function is executed with `sql_mode = ONLY_FULL_GROUP_BY`, the server can crash ([MDEV-31296](https://jira.mariadb.org/browse/MDEV-31296))
* When using two temporary tables in `OPTIMIZE TABLE`, executed as a prepared statement, the server can crash ([MDEV-31523](https://jira.mariadb.org/browse/MDEV-31523))
* When calling SP invoking another SP with a parameter requiring a type conversion, the server can crash ([MDEV-33270](https://jira.mariadb.org/browse/MDEV-33270))
* Possible hang when changing the InnoDB log file size using `SET GLOBAL innodb_log_file_size` (MENT-1271)
* If a query's `WHERE` clause has conditions over more than 128 columns of the same table, `optimizer_use_condition_selectivity` is 3, or higher, `use_stats_tables` is not set to `NEVER`, and statistics for the columns have been collected via `ANALYZE TABLE`, the server could crash (MENT-2036)

### Can result in unexpected behavior

* `SHOW WARNINGS` can show wrong foreign key related warnings/errors from an earlier transaction for InnoDB ([MDEV-32833](https://jira.mariadb.org/browse/MDEV-32833))
* `LeakSanitizer` errors in `mem_heap_create_block_func` upon query from `I_S.INNODB_SYS_TABLES` with `LIMIT ROWS EXAMINED` ([MDEV-32890](https://jira.mariadb.org/browse/MDEV-32890))
* Query from `I_S.INNODB_SYS_INDEXES` exceeding `LIMIT ROWS EXAMINED` causes `ER_UNKNOWN_ERROR` and `LeakSanitizer` errors in `rec_copy_prefix_to_buf_old` ([MDEV-28613](https://jira.mariadb.org/browse/MDEV-28613))
* Unexpected `ER_ERROR_ON_RENAME` upon `DROP` non-existing `FOREIGN KEY` with `ALGORITHM=COPY` ([MDEV-22230](https://jira.mariadb.org/browse/MDEV-22230))
* `FOREIGN_KEY_CHECKS` does not prevent non-copy alter from creating invalid FK structure ([MDEV-29092](https://jira.mariadb.org/browse/MDEV-29092))
* Secondary indexes on `VARCHAR` columns may be corrupted when the `VARCHAR` is extended so much that a column prefix index must be used ([MDEV-21245](https://jira.mariadb.org/browse/MDEV-21245))
* Spider: Valid `LEFT JOIN` results in `ERROR 1064` ([MDEV-26247](https://jira.mariadb.org/browse/MDEV-26247))
* Syntax error upon query with subquery from Spider table ([MDEV-30392](https://jira.mariadb.org/browse/MDEV-30392))
* Spider doesn't recognize `SEMI-JOIN` ([MDEV-31645](https://jira.mariadb.org/browse/MDEV-31645))
* `wsrep_provider_options` can be truncated on deep and long directory paths with diagnostics like: "Warning 1265 Data truncated for column 'VARIABLE\_VALUE' at row 1" in the server log ([MDEV-32634](https://jira.mariadb.org/browse/MDEV-32634))
* Mariadb-dump option `--delete-master-logs` is ignored ([MDEV-32953](https://jira.mariadb.org/browse/MDEV-32953))
* multi source replication filters breaking GTID semantic ([MDEV-26632](https://jira.mariadb.org/browse/MDEV-26632))
* If `wsrep_gtid_mode=ON` is used and `wsrep_gtid_domain_id` is non-zero, after SST using mariadb-backup GTIDs will become inconsistent both at the domain level, and at the seq\_no level ([MDEV-31905](https://jira.mariadb.org/browse/MDEV-31905))
* `wsrep_gtid_domain_id` is ignored on any node other than bootstrapped node when the `wsrep_gtid_mode` is set to ON ([MDEV-32740](https://jira.mariadb.org/browse/MDEV-32740))
* `LONG UNIQUE ... USING HASH` can result in an error when used with REPLACE ([MDEV-32839](https://jira.mariadb.org/browse/MDEV-32839))
* `JSON_ARRAYAGG()` doesn't evaluate correct charset which can lead to an unexpected result ([MDEV-24784](https://jira.mariadb.org/browse/MDEV-24784))
* `Performance_schema.status_by_thread` is missing SSL related entries, which also leads to an empty result set for `select * from sys.session_ssl_status`; ([MDEV-32751](https://jira.mariadb.org/browse/MDEV-32751))
* A connection can control `RAND()` in following connection if used in conjunction with `set rand_seed1, rand_seed2` ([MDEV-33148](https://jira.mariadb.org/browse/MDEV-33148))
* REGEXP\_REPLACE converts utf8mb4 supplementary characters to '?' ([MDEV-11777](https://jira.mariadb.org/browse/MDEV-11777))
* An `UPDATE` of a column of a `FEDERATED` table fails with "ERROR 1296 (HY000): Got error 10000 'Error on remote system: 1143: UPDATE command denied to user 'xxx'@'x.x.x.x' for column 'id' in table 'x'' from FEDERATED"

if the table includes an `AUTO_INCREMENT` column ([MDEV-32984](https://jira.mariadb.org/browse/MDEV-32984))

* "Read semi-sync reply magic number error" warnings are shown on the primary, if, first, the replica disables semi-synchronous mode (i.e., sets the variable rpl\_semi\_sync\_slave\_enabled=OFF) while an existing semi-sync connection is active, and then, the replica IO Thread stops (e.g., due to STOP SLAVE, or an error occurring) ([MDEV-32551](https://jira.mariadb.org/browse/MDEV-32551))
* `CHECK TABLE` shows a MyISAM/Aria table as corrupted, as a unique hash key on column prefix is computed incorrectly ([MDEV-29954](https://jira.mariadb.org/browse/MDEV-29954))
* mysql.slow\_log reports time when the query finished, not the start time ([MDEV-11628](https://jira.mariadb.org/browse/MDEV-11628))
* mariadb-upgrade does not remove mysql.plugin entries for plugins that became bundled. Error message "\[ERROR] mariadbd: Plugin 'unix\_socket' is already installed." is shown when upgrading ([MDEV-32043](https://jira.mariadb.org/browse/MDEV-32043))
* If storage engine Spider is loaded upon server startup, Spider related system, and status variables are not available (MENT-2043)
* Regular expressions cannot be used in queries on tables of type SPIDER ([MDEV-32986](https://jira.mariadb.org/browse/MDEV-32986))
* Memory leak when purging history of indexed virtual columns : ([MDEV-28682](https://jira.mariadb.org/browse/MDEV-28682))
* MariaDB Enterprise Backup sometimes shows the error `Can't open shared library '/file_key_management.so' (errno: 2, cannot open shared object file: No such file, or directory)` when the option `--target-dir` is not used with `--prepare` ([MDEV-29110](https://jira.mariadb.org/browse/MDEV-29110))
* The database part is not case sensitive in Stored Procedure names. This can lead to using the wrong stored procedure, if the same database name is used as lower, and uppercase ([MDEV-33019](https://jira.mariadb.org/browse/MDEV-33019))
* `CREATE UNIQUE INDEX` can fail with an incorrect `"ERROR 1286 (42000): Unknown storage engine 'partition'"` ([MDEV-21618](https://jira.mariadb.org/browse/MDEV-21618))
* After successful connection, server sets `SERVER_STATUS_AUTOCOMMIT` in `server_status` in the OK packet although the global variable `autocommit=0` is set ([MDEV-32875](https://jira.mariadb.org/browse/MDEV-32875))
* In some cases it is possible to create a Spider table which is referencing to a table on the same instance although `spider_same_server_link=0` is set ([MDEV-29718](https://jira.mariadb.org/browse/MDEV-29718))
* Spider fails to auto-discover a table structure with `ERROR 12500 (HY000): unknown` ([MDEV-33008](https://jira.mariadb.org/browse/MDEV-33008))
* On Windows the error `"InnoDB: Cannot open 'C:\xampp\mysql\data/ib_buffer_pool' for reading: No such file or directory"` could be shown ([MDEV-32983](https://jira.mariadb.org/browse/MDEV-32983))
* `REGEXP_REPLACE` treats empty strings different than `REPLACE` in `ORACLE` mode ([MDEV-29095](https://jira.mariadb.org/browse/MDEV-29095))
* `REPLACE` is supposed to remove all conflicting rows of a table. For `UNIQUE HASH, REPLACE` only removes the first conflicting row, not all conflicting rows ([MDEV-32837](https://jira.mariadb.org/browse/MDEV-32837))
* The SQL error plugin prints (`null`) as database if the mariadb client is not using any database to execute the SQL ([MDEV-32906](https://jira.mariadb.org/browse/MDEV-32906))
* The Enterprise Audit Plugin does not always report the user name (MENT-2035)

### Related to performance

* An `ALTER` using `ALGORITHM=INPLACE` or adding new indexes can increase the table space file size ([MDEV-26740](https://jira.mariadb.org/browse/MDEV-26740))
* History list is not shrunk unless there is a pause in the workload ([MDEV-33213](https://jira.mariadb.org/browse/MDEV-33213))
* Operations that involve extending InnoDB files can be extremely slow when the data directory resides on an NFS server that uses a smaller block size than 4096 bytes ([MDEV-32268](https://jira.mariadb.org/browse/MDEV-32268))
* When the size of the working set exceeds `innodb_buffer_pool_size`, the server can stall for short periods of time ([MDEV-33053](https://jira.mariadb.org/browse/MDEV-33053))
* Unnecessary writes of not modified undo log pages ([MDEV-33137](https://jira.mariadb.org/browse/MDEV-33137))
* `innodb_undo_log_truncate=ON` is blocking page writes ([MDEV-33112](https://jira.mariadb.org/browse/MDEV-33112))
* `innodb_undo_log_truncate=ON` prevents fast shutdown ([MDEV-33062](https://jira.mariadb.org/browse/MDEV-33062))
* Some calls to `buf_read_ahead_linear()` seem to be useless ([MDEV-32068](https://jira.mariadb.org/browse/MDEV-32068))
* Opening all `.ibd` files on InnoDB startup can be slow ([MDEV-32027](https://jira.mariadb.org/browse/MDEV-32027))
* Adaptive flush recommendation ignores dirty ratio and checkpoint age ([MDEV-31939](https://jira.mariadb.org/browse/MDEV-31939))
* Possible slowdown when running nested statement with many partitions (MENT-2047)
* Performance regression due to frequent scan of full `buf_pool.flush_list` (MENT-2051)

## Platforms

In alignment to the [enterprise lifecycle](../enterprise-server-lifecycle.md), MariaDB Enterprise Server 10.6.17-12 is provided for:

* AlmaLinux 8 (x86\_64, ARM64)
* AlmaLinux 9 (x86\_64, ARM64)
* CentOS 7 (x86\_64)
* Debian 10 (x86\_64, ARM64)
* Debian 11 (x86\_64, ARM64)
* Debian 12 (x86\_64, ARM64)
* Microsoft Windows (x86\_64) (MariaDB Enterprise Cluster excluded)
* Red Hat Enterprise Linux 7 (x86\_64)
* Red Hat Enterprise Linux 8 (x86\_64, ARM64)
* Red Hat Enterprise Linux 9 (x86\_64, ARM64)
* Rocky Linux 8 (x86\_64, ARM64)
* Rocky Linux 9 (x86\_64, ARM64)
* SUSE Linux Enterprise Server 12 (x86\_64)
* SUSE Linux Enterprise Server 15 (x86\_64, ARM64)
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
