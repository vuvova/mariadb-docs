# Connector/J 2.4.3 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/#connectors)[Release Notes](mariadb-connector-j-243-release-notes.md)[Changelog](../changelogs/2.4/mariadb-connector-j-243-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 5 Aug 2019

MariaDB Connector/J 2.4.3 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_\
release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

## Notes

New option `blankTableNameMeta` permit to have Resultset metadata getTableName methods always return blank in place of returning real table name as JDBC indicate. This is for ease migration from Oracle since Oracle driver always returns an empty string.

* [CONJ-717](https://jira.mariadb.org/browse/CONJ-717): conversion function support for other data types than default MariaDB conversion type
* [CONJ-722](https://jira.mariadb.org/browse/CONJ-722): Permit suppression of result-set metadata getTableName for oracle compatibility
* [CONJ-719](https://jira.mariadb.org/browse/CONJ-719): Saving values using Java 8 LocalTime does not store fractional parts of seconds
* [CONJ-716](https://jira.mariadb.org/browse/CONJ-716): Correcting possible NPE on non-thread safe NumberFormat (logging)

## Changelog

For a complete list of changes made in MariaDB Connector/J 2.4.3, with links to detailed\
information on each push, see the [changelog](../changelogs/2.4/mariadb-connector-j-243-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
