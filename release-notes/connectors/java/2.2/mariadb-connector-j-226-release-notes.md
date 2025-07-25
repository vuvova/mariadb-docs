# Connector/J 2.2.6 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.2.6/)[Release Notes](mariadb-connector-j-226-release-notes.md)[Changelog](../changelogs/2.2/mariadb-connector-j-226-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 19 Jul 2018

MariaDB Connector/J 2.2.6 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_\
release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

## Minor change:

* \[[CONJ-623](https://jira.mariadb.org/browse/CONJ-623)] Increase connection logging when Primary node connection fails
* \[[CONJ-384](https://jira.mariadb.org/browse/CONJ-384)] Permit knowing affected rows number, not only real changed rows

## Bug correction:

* \[[CONJ-624](https://jira.mariadb.org/browse/CONJ-624)] MariaDbPoolDataSource possible NPE on configuration getter
* \[[CONJ-622](https://jira.mariadb.org/browse/CONJ-622)] The option "connectTimeout" must take in account DriverManager.getLoginTimeout() when set
* \[[CONJ-621](https://jira.mariadb.org/browse/CONJ-621)] wrong escaping when having curly bracket in table/field name
* \[[CONJ-618](https://jira.mariadb.org/browse/CONJ-618)] Client preparestatement parsing error on escaped ' / " in query

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
