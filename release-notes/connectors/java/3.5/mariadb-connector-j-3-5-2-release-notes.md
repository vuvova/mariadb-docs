# Connector/J 3.5.2 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](mariadb-connector-j-3-5-2-release-notes.md)[Changelog](../changelogs/3.5/mariadb-connector-j-3-5-2-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 11 Feb 2025

MariaDB Connector/J 3.5.2 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

## Notable change

* [CONJ-1229](https://jira.mariadb.org/browse/CONJ-1229) Permit executeQuery commands to not return a result-set

## Bugs Fixed

* [CONJ-1228](https://jira.mariadb.org/browse/CONJ-1228) The method result-set.getObject(val) for a field of type BLOB returns an object of type Blob by default instead of the expected object of type byte\[].
  * The following methods are not affected
    * resultset.getBytes(val)
    * resultset.getBlob(val)
    * resultset.getObject(val, byte\[].class)
    * resultset.getObject(val, Blob.class)\
      all returns expected type)
* [CONJ-1225](https://jira.mariadb.org/browse/CONJ-1225) System throws an SQLTimeoutException prematurely without checking all available connections
* [CONJ-1221](https://jira.mariadb.org/browse/CONJ-1221) DatabaseMetadata.getTypeInfo() is missing the data types UUID and VECTOR
* [CONJ-1218](https://jira.mariadb.org/browse/CONJ-1218) Incorrect behavior where XA connections are closed when regular connections are terminated - this is against JDBC specifications
* [CONJ-1217](https://jira.mariadb.org/browse/CONJ-1217) When using the parameter trustCertificateKeyStorePassword, alias for trustStorePassword, an exception is thrown
* [CONJ-660](https://jira.mariadb.org/browse/CONJ-660) The connection option `disconnectOnExpiredPasswords` was not handled by the connector..It controls the client behavior when connecting with an expired password.
  * When set to true (default), the client disconnects if it detects an expired password.
  * When false, the client maintains the connection and allows setting a new password.

## Changelog

For a complete list of changes made in MariaDB Connector/J 3.5.2, with links to detailed\
information on each push, see the [changelog](../changelogs/3.5/mariadb-connector-j-3-5-2-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
