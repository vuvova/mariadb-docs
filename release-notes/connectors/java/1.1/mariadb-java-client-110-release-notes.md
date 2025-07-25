# Connector/J 1.1.0 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/client-java/1.1.0/) | **Release Notes** | [Changelog](../changelogs/1.1/mariadb-java-client-110-changelog.md)

**Release date:** 15 Jan 2013

MariaDB Java Client 1.1.0 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_\
release. In general this means that there are no known serious bugs,\
except for those marked as feature requests, that no bugs were fixed\
since last release that caused a notable code changes, and that we\
believe the code is ready for general usage (based on bug inflow).

**For a description of the MariaDB Java Client see the**[**About the MariaDB Java Client**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-the-mariadb-java-client/README.md) **page.**

For a list of changes made in this release, with links to detailed\
information on each push, see the [changelog](../changelogs/1.1/mariadb-java-client-110-changelog.md).

Here is a list of the important changes in this release

* Implemented several missing methods in DatabaseMetaData ([CONJ-11](https://jira.mariadb.org/browse/CONJ-11))\
  Implementation for these methods was missing in the past and is now corrected :
  * [DatabaseMetaData.getTypeInfo()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getTypeInfo\(\))
  * [DatabaseMetaData.getProcedures()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getProcedures\(java.lang.String,%20java.lang.String,%20java.lang.String\))
  * [DatabaseMetaData.getFunctions()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getFunctions\(java.lang.String,_java.lang.String,_java.lang.String\))
  * [DatabaseMetaData.getProcedureColumns()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getProcedureColumns\(java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String\))
  * [DatabaseMetaData.getFunctionColumns()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getFunctionColumns\(java.lang.String,%20java.lang.String,%20java.lang.String,_java.lang.String\))
  * [DatabaseMetaData.getSuperTables()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getSuperTables\(java.lang.String,%20java.lang.String,%20java.lang.String\)) (implementation returns 0 rows,but correct result set metadata)
  * [DatabaseMetaData.getSuperTypes()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getSuperTypes\(java.lang.String,%20java.lang.String,%20java.lang.String\)) (implementation returns 0 rows, but correct result set metadata)
* Consistent, compatible with ConnectorJ handling of JDBC catalogs vs schemas vs databases ([CONJ-10](https://jira.mariadb.org/browse/CONJ-10), [CONJ-9](https://jira.mariadb.org/browse/CONJ-9), [CONJ-8](https://jira.mariadb.org/browse/CONJ-8))\
  All DatabaseMetaData methods that return catalog or schema name, or accept catalog or schema as input parameter, will handle catalog input parameter as database name, and will return current database name in the "TABLE\_CAT" column and null for "TABLE\_SCHEM" column. This handling is consistent with ConnectorJ handling for catalogs.\
  Here is the list of affected methods :
  * [DatabaseMetaData.getTables()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getTables\(java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String\[]\))
  * [DatabaseMetaData.getColumns()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getColumns\(java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String\))
  * [DatabaseMetaData.getColumnPrivileges()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getColumnPrivileges\(java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String\))
  * [DatabaseMetaData.getTablePrivileges()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getTablePrivileges\(java.lang.String,%20java.lang.String,%20java.lang.String\))
  * [DatabaseMetaData.getPrimaryKeys()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getPrimaryKeys\(java.lang.String,%20java.lang.String,%20java.lang.String\))
  * [DatabaseMetaData.getImportedKeys()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getImportedKeys\(java.lang.String,%20java.lang.String,%20java.lang.String\))
  * [DatabaseMetaData.getExportedKeys()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getExportedKeys\(java.lang.String,%20java.lang.String,%20java.lang.String\))
  * [DatabaseMetaData.getCrossReference()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getCrossReference\(java.lang.String,%20java.lang.String,%20java.lang.String,_java.lang.String,_java.lang.String,%20java.lang.String\))
  * [DatabaseMetaData.getIndexInfo()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#getIndexInfo\(java.lang.String,%20java.lang.String,%20java.lang.String,%20boolean,%20boolean\))
  * [ResultSetMetaData.getCatalogName()](https://docs.oracle.com/javase/7/docs/api/java/sql/ResultSetMetaData.html#getCatalogName\(int\)) will now return database name
  * [ResultSetMetaData.getSchemaName()](https://docs.oracle.com/javase/7/docs/api/java/sql/ResultSetMetaData.html#getSchemaName\(int\)) will return an empty string.
  * Methods [DatabaseMetaData.supportsSchemasInDataManipulation()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#supportsSchemasInDataManipulation\(\)), [DatabaseMetaData.supportsSchemasInTableDefinitions()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#supportsSchemasInTableDefinitions\(\)), [DatabaseMetaData.supportsSchemasInPrivilegeDefinitions()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#supportsSchemasInPrivilegeDefinitions\(\)) will return false indicating that schemas are not supported. [DatabaseMetaData.supportsCatalogsInDataManipulation()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#supportsCatalogsInDataManipulation\(\)),[DatabaseMetaData.supportsCatalogsInTableDefinitions()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#supportsCatalogsInTableDefinitions\(\)), [DatabaseMetaData.supportsCatalogsInPrivilegeDefinitions()](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html#supportsCatalogsInPrivilegeDefinitions\(\)) all return true (catalogs are supported).
* Handling of statement timeout is now fixed ([CONJ-1](https://jira.mariadb.org/browse/CONJ-1))\
  Prior implementation was based on socket timeouts and did not work well due to a Java bug (socket can't recover after a timeout)
* Driver can be used in OSGi environments now - it includes OSGi-specific entries in MANIFEST.MF ([CONJ-2](https://jira.mariadb.org/browse/CONJ-2))
* Support dumpQueriesOnException=true in the JDBC URL ([CONJ-12](https://jira.mariadb.org/browse/CONJ-12)) . The effect of this parameter is such that query text is included into exception message. Additionally, query text is dumped on MySQL syntax errors, no matter if this parameter is set or not.
* It is now possible to use IPv6 addresses with the connector using [RFC2732](https://www.ietf.org/rfc/rfc2732.txt) syntax with square brakets, for example jdbc:mysql:\[::1]:3306 for IPv6-capable server running on local machine, port 3306\
  ([CONJ-7](https://jira.mariadb.org/browse/CONJ-7))
* SSL support. useSSL=true parameter is now functional. Additionally, trustServerCertificates=true can be set, to avoid checking server certificate validity.
* sessionVariables driver URL parameter is now supported.
* LOAD DATA LOCAL INFILE can use generic URLs (e.g http) for file specification
* SQL Comments are not stripped anymore off PreparedStatements.
* Fixed ArrayOutOfBounds exception when parsing JDBC ([CONJ-4](https://jira.mariadb.org/browse/CONJ-4))
* Fixed exception in Connection.getWarnings(), which was throws is connection was closed

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
