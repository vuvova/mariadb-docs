# MariaDB 10.2.17 Release Notes

The most recent release of [MariaDB 10.2](what-is-mariadb-102.md) is:[**MariaDB 10.2.44**](mariadb-10244-release-notes.md) Stable (GA) [Download Now](https://downloads.mariadb.org/mariadb/10.2.44/)

[Download](https://downloads.mariadb.org/mariadb/10.2.17)[Release Notes](mariadb-10217-release-notes.md)[Changelog](../../changelogs/changelogs-mariadb-102-series/mariadb-10217-changelog.md)[Overview of 10.2](what-is-mariadb-102.md)

**Release date:** 14 Aug 2018

[MariaDB 10.2](what-is-mariadb-102.md) is the previous stable series of MariaDB. It is an evolution\
of [MariaDB 10.1](../release-notes-mariadb-10-1-series/changes-improvements-in-mariadb-10-1.md) with several entirely new features not found anywhere else\
and with backported and reimplemented features from MySQL 5.6 and 5.7.

[MariaDB 10.2.17](mariadb-10217-release-notes.md) is a [_**Stable (GA)**_](../../about/release-criteria.md) release.

**For an overview of** [**MariaDB 10.2**](what-is-mariadb-102.md) **see the**[**What is MariaDB 10.2?**](what-is-mariadb-102.md) **page.**

Upgrading from earlier 10.2.x versions is **highly recommended** for all **Galera** users due to bug [MDEV-12837](https://jira.mariadb.org/browse/MDEV-12837) which caused serious stability issues with earlier versions. See the bug issue page for more information.

Thanks, and enjoy MariaDB!

## Notable Changes

* New variable [innodb\_log\_optimize\_ddl](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables) for avoiding delay due to page flushing and allowing concurrent backup
* New variable, [core\_file](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#core_file) for specifying whether to write a core file on crash.
* [InnoDB](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb) updated to 5.7.23
* ALTER TABLE fixes:
  * [MDEV-14637](https://jira.mariadb.org/browse/MDEV-14637) - Fix hang due to DDL with FOREIGN KEY or persistent statistics
  * [MDEV-15953](https://jira.mariadb.org/browse/MDEV-15953) - Alter InnoDB Partitioned Table Moves Files (which were originally not in the datadir) to the datadir
  * [MDEV-16515](https://jira.mariadb.org/browse/MDEV-16515) - InnoDB: Failing assertion: ++retries < 10000 in file dict0dict.cc line 2737
  * [MDEV-16809](https://jira.mariadb.org/browse/MDEV-16809) - Allow full redo logging for ALTER TABLE
* Temporary tables: [MDEV-16713](https://jira.mariadb.org/browse/MDEV-16713) - InnoDB hang with repeating log entry
* [MDEV-16596](https://jira.mariadb.org/browse/MDEV-16596) - Windows - redo log does not work on native 4K sector disks
* indexed virtual columns: [MDEV-15855](https://jira.mariadb.org/browse/MDEV-15855) - Deadlock between purge thread and DDL statement
* locking: [MDEV-16664](https://jira.mariadb.org/browse/MDEV-16664) - Change the default to innodb\_lock\_schedule\_algorithm=fcfs
* Galera: [MDEV-15822](https://jira.mariadb.org/browse/MDEV-15822) - WSREP: BF lock wait long for trx
* Packages and a repository for openSUSE 15 have been added with this release, visit the [Repository Configuration Tool](https://downloads.mariadb.org/mariadb/repositories/) for instructions on adding the repository
* Fixes for the following [security vulnerabilities](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/security):
  * [CVE-2018-3060](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-3060)
  * [CVE-2018-3064](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-3064)
  * [CVE-2018-3063](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-3063)
  * [CVE-2018-3058](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-3058)
  * [CVE-2018-3066](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-3066)

When upgrading from [MariaDB 10.2.16](mariadb-10216-release-notes.md) or earlier to [MariaDB 10.2.17](mariadb-10217-release-notes.md) or higher,\
running [mysql\_upgrade](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/legacy-clients-and-utilities/mysql_upgrade) is **required** due to changes introduced in[MDEV-14637](https://jira.mariadb.org/browse/MDEV-14637).

## Changelog

For a complete list of changes made in [MariaDB 10.2.17](mariadb-10217-release-notes.md) with links to detailed\
information on each push, see the [changelog](../../changelogs/changelogs-mariadb-102-series/mariadb-10217-changelog.md).

## Contributors

For a full list of contributors to [MariaDB 10.2.17](mariadb-10217-release-notes.md), see the [MariaDB Foundation release announcement](https://mariadb.org/mariadb-10-2-17-now-available/).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
