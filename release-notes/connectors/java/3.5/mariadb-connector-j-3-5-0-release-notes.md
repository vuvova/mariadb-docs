# Connector/J 3.5.0 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](mariadb-connector-j-3-5-0-release-notes.md)[Changelog](../changelogs/3.5/mariadb-connector-j-3-5-0-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 24 Oct 2024

MariaDB Connector/J 3.5.0 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md) **page**

The MariaDB Connector/J 3.5 release series is replacing the maintenance releases for the 3.4 release series, as the new release series is fully compatible with 3.4.

## Notable changes

### PARSEC Authentication - [CONJ-1193](https://jira.mariadb.org/browse/CONJ-1193)

Support of the PARSEC Authentication Plugin which is provided starting with MariaDB Server 11.6. See [parsec documentation](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/plugins/authentication-plugins/authentication-plugin-parsec) for more details.

This requires java 15+ (to use java native ed25519 Algorithm implementation).\
For previous versions of java, this will require adding BouncyCastle as dependency.

### New options `truststore`, `trustStorePassword` and `trustStoreType` - [CONJ-1183](https://jira.mariadb.org/browse/CONJ-1183)

Those options permit the use of a specific truststore that differs from the Java default truststore. This has been added for MariaDB 2.x and MySQL connector compatibility. See [documentation](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-j/using-tls-ssl-with-mariadb-java-connector#java-default-truststore)

### New option `connectionCollation` - [CONJ-1199](https://jira.mariadb.org/browse/CONJ-1199)

The Connector is using the utf8mb4 charset per default when establishing a connection. ‘connectionCollation’ can be used to define which utf8mb4 collation should be used. If not set the server default collation for utf8mb4 will be used.

Starting with [MariaDB 11.4](../../../community-server/mariadb-11-4-series/what-is-mariadb-114.md) we recommend to instead set [character\_set\_collations](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#character_set_collations)

### Support for methods setObject/getObject and setArray/getArray - [CONJ-1205](https://jira.mariadb.org/browse/CONJ-1205)

This addition is a preparation for the Vector support of MariaDB Server

Example of Array:

```java
Array valArray = connection.createArrayOf("float", new float[] {1, 2, 3}); 
try (PreparedStatement prep = 
connection.prepareStatement("INSERT INTO BinaryCodec(t0, t1) VALUES (?, ?, ?)")) { 
prep.setInt(1, 1); 
prep.setArray(2, valArray); 
prep.setObject(3, new float[] {4, 5, 6}); 
prep.execute(); 
}
```

Resultset:

```java
Array resArray = rs.getArray(2); 
float[] res = rs.getObject(2, float[].class);
```

## Bugs Fixed

* [CONJ-1202](https://jira.mariadb.org/browse/CONJ-1202) A change of the collation via a session variable might be ignored
* [CONJ-1201](https://jira.mariadb.org/browse/CONJ-1201) Incorrect default behavior for forceConnectionTimeZoneToSession
  * NOTE: If client and server use different time zones and no timezone options where used, MariaDB Connector/J 3.4 introduces a change which is forcing client timezone to the session. This behavior is an not intended incompatibility change compared to MariaDB Connector/J 3.3, which is corrected in MariaDB Connector/J 3.5 with this change
* [CONJ-1200](https://jira.mariadb.org/browse/CONJ-1200) Batch import fails with exception "Unknown command"
* [CONJ-1187](https://jira.mariadb.org/browse/CONJ-1187) Throw exception type SQLTimeoutException instead of SQLNonTransientConnectionException for connection timeouts

## Changelog

For a complete list of changes made in MariaDB Connector/J 3.5.0, with links to detailed\
information on each push, see the [changelog](../changelogs/3.5/mariadb-connector-j-3-5-0-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
