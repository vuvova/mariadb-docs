# Connector/J 1.5.8 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/1.5.8/)[Release Notes](mariadb-connector-j-158-release-notes.md)[Changelog](../changelogs/1.5/mariadb-connector-j-158-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 15 Feb 2017

MariaDB Connector/J 1.5.8 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_\
release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md) **page**

## Notable Changes

This version is a bug-fix release.

### Bugfix

* [CONJ-424](https://jira.mariadb.org/browse/CONJ-424) : getGeneratedKeys() on table without generated key failed on second execution
* [CONJ-412](https://jira.mariadb.org/browse/CONJ-412) : Metadata take in account tinyInt1isBit in method columnTypeClause
* [CONJ-418](https://jira.mariadb.org/browse/CONJ-418) : ResultSet.last() isLast() afterLast() and isAfterLast() correction when streaming
* [CONJ-415](https://jira.mariadb.org/browse/CONJ-415) : ResultSet.absolute() should not always return true
* [CONJ-392](https://jira.mariadb.org/browse/CONJ-392) : Aurora cluster endpoint detection fails when time\_zone doesn't match system\_time\_zone
* [CONJ-425](https://jira.mariadb.org/browse/CONJ-425) : CallableStatement getObject class according to java.sql.Types value
* [CONJ-426](https://jira.mariadb.org/browse/CONJ-426) : Allow executeBatch to be interrupted
* [CONJ-420](https://jira.mariadb.org/browse/CONJ-420) : High CPU usage against Aurora after 2 hours inactivity

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
