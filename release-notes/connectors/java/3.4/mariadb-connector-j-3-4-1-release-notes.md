# Connector/J 3.4.1 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](mariadb-connector-j-3-4-1-release-notes.md)[Changelog](../changelogs/3.4/mariadb-connector-j-3-4-1-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 17 Jul 2024

MariaDB Connector/J 3.4.1 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md) **page**

## Notable Changes

### Implementation of pinGlobalTxToPhysicalConnection for XA Connection

For [CONJ-1189](https://jira.mariadb.org/browse/CONJ-1189)

The new boolean option `pinGlobalTxToPhysicalConnection`, when enabled, ensures that an operation for a specific XID is routed to the same connection, to permit supporting `XA START <xid>` when XA END has been called.\
This prevent errors like

```
XA resource 'xaDataSource': resume for XID 'XID: <some id>' raised -5: invalid arguments were given for the XA operation
```

### Enhanced host description

For [CONJ-685](https://jira.mariadb.org/browse/CONJ-685)/[CONJ-686](https://jira.mariadb.org/browse/CONJ-686)

The host description for connecting to the server has been changed from either `<host>[:<portnumber>]` or `address=(host=<host>)[(port=<portnumber>)][(type=(master|slave))]`\
to a more detaild host description, permitting to set localsocket or pipe, and to define a specific ssl mode depending on the host. New format:

```
address=(host=<host>|localSocket=<socket>|pipe=<namedpipe>)[(port=<portnumber>)][(type=(master|slave))][(sslMode=disable|trust|verify-ca|verify-full)]
```

Example:

```java
jdbc:mariadb:sequential://address=(localSocket=/socket),address=(host=10.0.0.1)(port=3306)(sslMode=verify-full)/DB
```

This connection string now permits to use a local unix socket if available, and host 10.0.0.1 with ssl if the unix socket is not available.\
A detailed host description option supersedes a global option description. The previous example can also be written in the following way, defining different ssl modes for both host options:

```java
jdbc:mariadb:sequential://address=(localSocket=/socket)(sslMode=disable),10.0.0.1:3306/DB?sslMode=verify-full
```

### Adding databaseTerm alias

For [CONJ-1190](https://jira.mariadb.org/browse/CONJ-1190)

Option `useCatalogTerm` has an alias `databaseTerm` for MySQL connector compatibility.

## Bugs Fixed

* [CONJ-1181](https://jira.mariadb.org/browse/CONJ-1181) The validation of a statement of the cache for prepared statements is not taking the use of different schemas into account, which can result in unexpected behavior when the same statement is executed on different schemas.
* [CONJ-1178](https://jira.mariadb.org/browse/CONJ-1178) DatabaseMetaData.getImportedKeys returns a different PK\_NAME value than DatabaseMetaData.getExportedKeys when using a NON UNIQUE constraint.
* [CONJ-1180](https://jira.mariadb.org/browse/CONJ-1180) Slow performance of function DatabaseMeta.getExportedKeys()
* [CONJ-1185](https://jira.mariadb.org/browse/CONJ-1185) Android app incompatibility, regex CANON\_EQ flag is not supported on Android OS
* [CONJ-1188](https://jira.mariadb.org/browse/CONJ-1188) Database meta getSQLKeywords is listing all reserved keywords, not only the restricted keywords
* [CONJ-1191](https://jira.mariadb.org/browse/CONJ-1191) The Function metadata getImportedKeys is slow when a database has not been set
* [CONJ-1068](https://jira.mariadb.org/browse/CONJ-1068) The Function ResultSetMetaData.getColumnTypeName() returns type VARCHAR instead of type TINYTEXT for columns of type TINYTEXT
* [CONJ-1182](https://jira.mariadb.org/browse/CONJ-1182) Missing error mapping for errors XA\_RBTIMEOUT, XA\_RBTIMEOUT and XA\_RBDEADLOCK

## Changelog

For a complete list of changes made in MariaDB Connector/J 3.4.1, with links to detailed\
information on each push, see the [changelog](../changelogs/3.4/mariadb-connector-j-3-4-1-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
