# MariaDB 10.6.3 Release Notes

{% include "../../.gitbook/includes/latest-10-6.md" %}

<a href="https://downloads.mariadb.org/mariadb/10.6.3/" class="button primary">Download</a> <a href="mariadb-1063-release-notes.md" class="button secondary">Release Notes</a> <a href="../changelogs/changelogs-mariadb-106-series/mariadb-1063-changelog.md" class="button secondary">Changelog</a> <a href="what-is-mariadb-106.md" class="button secondary">Overview of 10.6</a>

**Release date:** 6 Jul 2021

[MariaDB 10.6](what-is-mariadb-106.md) is the current stable series of MariaDB. It is an evolution\
of [MariaDB 10.5](../old-releases/mariadb-10-5-series/what-is-mariadb-105.md) with several entirely new features.

[MariaDB 10.6.3](mariadb-1063-release-notes.md) is a [_**Stable (GA)**_](../about/release-criteria.md) release.

Thanks, and enjoy MariaDB!

## Notable Changes

### InnoDB

* Maximum value of [innodb\_lock\_wait\_timeout](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_lock_wait_timeout) is now 100000000, which means infinite timeout ([MDEV-26067](https://jira.mariadb.org/browse/MDEV-26067))
* Write performance improvements: [MDEV-25954](https://jira.mariadb.org/browse/MDEV-25954), [MDEV-25948](https://jira.mariadb.org/browse/MDEV-25948), [MDEV-25113](https://jira.mariadb.org/browse/MDEV-25113), [MDEV-26004](https://jira.mariadb.org/browse/MDEV-26004), [MDEV-25801](https://jira.mariadb.org/browse/MDEV-25801)
* [Atomic DDL](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-definition/atomic-ddl) rewrite ([MDEV-25506](https://jira.mariadb.org/browse/MDEV-25506))
* Thinly provisioned SSD support for page\_compressed tables ([MDEV-26029](https://jira.mariadb.org/browse/MDEV-26029))

### Replication

* Fix binlog background thread hang at shutdown ([MDEV-26031](https://jira.mariadb.org/browse/MDEV-26031))

### General

* The views [INFORMATION\_SCHEMA.KEYWORDS](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/information-schema/information-schema-tables/information-schema-keywords-table) and [INFORMATION\_SCHEMA.SQL\_FUNCTIONS](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/information-schema/information-schema-tables/information-schema-sql_functions-table) have been added to the information schema ([MDEV-25129](https://jira.mariadb.org/browse/MDEV-25129))
* Assertion \`\`thd->locked\_tables\_mode == LTM\_NONE'`failed in`Locked\_tables\_list::init\_locked\_tables\` ([MDEV-25837](https://jira.mariadb.org/browse/MDEV-25837))

### Security

* Fixes for the following [security vulnerabilities](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/security):
  * [CVE-2021-35604](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-35604)
  * [CVE-2021-46658](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-46658)

## Changelog

For a complete list of changes and bugfixes made in [MariaDB 10.6.3](mariadb-1063-release-notes.md), with links to detailed\
information on each push, see the [changelog](../changelogs/changelogs-mariadb-106-series/mariadb-1063-changelog.md).

## Contributors

For a full list of contributors to [MariaDB 10.6.3](mariadb-1063-release-notes.md), see the [MariaDB Foundation release announcement](https://mariadb.org/mariadb-10-6-3-ga-now-available/).

{% include "../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
