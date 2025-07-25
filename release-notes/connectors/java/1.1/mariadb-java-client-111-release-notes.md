# Connector/J 1.1.1 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/client-java/1.1.1/) | **Release Notes** | [Changelog](../changelogs/1.1/mariadb-java-client-111-changelog.md) |[Java Client Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-the-mariadb-java-client/README.md)

**Release date:** 01 Mar 2013

MariaDB Java Client 1.1.1 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_\
release. In general this means that there are no known serious bugs,\
except for those marked as feature requests, that no bugs were fixed\
since last release that caused a notable code changes, and that we\
believe the code is ready for general usage (based on bug inflow).

**For a description of the MariaDB Java Client see the**[**About the MariaDB Java Client**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-the-mariadb-java-client/README.md) **page.**

For a list of changes made in this release, with links to detailed\
information on each push, see the [changelog](../changelogs/1.1/mariadb-java-client-111-changelog.md).

### New functionality in this release

* Implement tcpAbortiveClose option, for "hard" socket close ([CONJ-27](https://jira.mariadb.org/browse/CONJ-27))
  * This option can be used in environments where connections are created and closed in rapid succession. Often, it is not possible to create a socket in such environment after a while, since all local "ephemeral" ports are used up by TCP connections in TCP\_WAIT state. Using tcpAbortiveClose works around this problem by resetting TCP connections rather (abortive or hard close) than doing an orderly close. It is accomplished by using socket.setSoLinger(true,0) for abortive close.

### Bugs fixed in this release

* MySQLStatement will now indicate there are no more results by returning -1 from getUpdateCount() and null from getResultSet(),as mandated by the standard ([CONJ-14](https://jira.mariadb.org/browse/CONJ-14))
* Introduced nullCatalogMeansCurrent parameter for compatibly with ConnectorJ, and make it default ([CONJ-16](https://jira.mariadb.org/browse/CONJ-16))
  * Prior to this change, DatabaseMetadata.getTables() or other methods of DatabaseMetaData that accept catalog names and return result sets would treat null as prescribed by the JDBC standard (null means no restriction which catalog is used). This behavior is now changed for the sake of compatibility. Starting with 1.1.1 , null for catalog name will mean current catalog. To get JDBC standard behavior, one needs to set nullCatalogMeansCurrent=false.
* DatabaseMedataData.getColumns() returned incorrect values in the "COLUMN\_SIZE" column for character data.([CONJ-15](https://jira.mariadb.org/browse/CONJ-15)))
  * Prior to the change, octet size was returned (length in bytes). Depending on the character set used, it could be 3 times bigger than the length in characters that was specified by CREATE or ALTER table. This behavior is corrected in 1.1.1
* DatabaseMetaData.getColumns() always handled MySQL YEAR datatype as SMALLINT. ([CONJ-19](https://jira.mariadb.org/browse/CONJ-19))
  * The behavior is now fixed and getColumns returns either DATE or SMALLINT depending on how the 'yearIsDateType' parameter is set.
* ResultSetMetaData.getColumnName() returned an empty string in special cases ([CONJ-17](https://jira.mariadb.org/browse/CONJ-17))
  * ResultSetMetaData.getColumnName() returned and empty string for "non-columns" in a result set (functions, aggregates like count(\*), and so on). The fix is to return the column label to be returned if the column name is empty.
* Ensure that getObject() returns byte array for CHAR BINARY.([CONJ-20](https://jira.mariadb.org/browse/CONJ-20))
  * Also make sure that getColumnType(),getColumnClassName(),getColumnTypeName() return values indicate BINARY for fixed binary type.
* JVM does not exit if statement timeout is used.([CONJ-23](https://jira.mariadb.org/browse/CONJ-23))
  * Constructor for Timer was corrected to ensure that the Timer thread has type background thread. Thus Timer won't prevent JVM from exiting.
* Calling first() on "streaming" result set and using the result set afterwards generated NullPointerException ([CONJ-24](https://jira.mariadb.org/browse/CONJ-24))
  * Now a SQLException is thrown early on, in the first() call, since streaming results sets are not scrollable.
* Connection.close() hangs if there is an open streaming result set, and next() was not called on this result set ([CONJ-25](https://jira.mariadb.org/browse/CONJ-25))

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
