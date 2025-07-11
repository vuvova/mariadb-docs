# MariaDB Java Client 1.1.0 Changelog

The most recent [_**Stable**_](../../../../mariadb-release-criteria.md) _**(GA)**_ release of [MariaDB Connector/J](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) is:[**MariaDB Connector/J 3.5.3**](../../mariadb-connector-j-3-5-release-notes/mariadb-connector-j-3-5-3-release-notes.md)

[Download](https://downloads.mariadb.org/client-java/1.1.0/) | [Release Notes](../../mariadb-connector-j-11-release-notes/mariadb-java-client-110-release-notes.md) | **Changelog**

**Release date:** 15 Jan 2013

For the highlights of this release, see the [release notes](../../mariadb-connector-j-11-release-notes/mariadb-java-client-110-release-notes.md).

The revision number links will take you to the revision's page on Launchpad. On Launchpad you can view more details of the revision and view diffs of the code modified in that revision.

* [Revision #394](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/394)\
  Tue 2013-01-15 02:23:23 +0100
  * safer number truncation with ResultSet.getInt(), ResultSet.getLong() and ResultSet.getShort()
* [Revision #393](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/393)\
  Tue 2013-01-15 02:22:15 +0100
  * For Boolean data type BIT(1), ResultSet.getString() should return either "true" or "false", not unprintable string with single byte 0x1 or 0x0
* [Revision #392](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/392)\
  Tue 2013-01-15 02:18:28 +0100
  * [CONJ-13](https://jira.mariadb.org/browse/CONJ-13), [CONJ-11](https://jira.mariadb.org/browse/CONJ-11) - implement DatabaseMetaData.getTypeInfo()
* [Revision #391](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/391)\
  Mon 2013-01-14 00:15:13 +0100
  * improve several DatabaseMetaData methods : - fallback to empty result set for getProcedureColumns/getFunctionColumns if I\_S.parameters not available (a better fallbac might be implemented in the future) - getProcedures returns now also functions (compatibility with ConnectorJ) - getColumns() now handles unsigned types correctly (since JDBC does not have anything unsigned, returned data type for "unsigned" is the bigger numeric type) - MySQLProtocol is extended with version-related functions - getMajorServerVersion(), getMinorServerVersion(), getPatchServerVersion() - MySQLResultSet returns empty schema name, but non-empty catalog name, for consistency with the rest of the driver.
* [Revision #390](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/390)\
  Sat 2013-01-12 19:27:29 +0100
  * Fix driver version
* [Revision #389](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/389)\
  Sat 2013-01-12 19:27:13 +0100
  * Remove sqlEscapeString, it is duplicate of already existing escapeString
* [Revision #388](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/388)\
  Sat 2013-01-12 19:24:05 +0100
  * Fix findColumn() - the string parameter is meant to be column label, and only if label is missing column name It was implemented other way around
* [Revision #387](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/387)\
  Sat 2013-01-12 19:23:15 +0100
  * [CONJ-11](https://jira.mariadb.org/browse/CONJ-11) - implemented getProcedureColumns and getFunctionColumns
* [Revision #386](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/386)\
  Sat 2013-01-12 00:29:16 +0100
  * Remove unused variable
* [Revision #385](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/385)\
  Sat 2013-01-12 00:27:01 +0100
  * [CONJ-11](https://jira.mariadb.org/browse/CONJ-11), [CONJ-12](https://jira.mariadb.org/browse/CONJ-12) : Rework MySQLDatabaseMetaData. - Implement getProcedures() and getFunction(). - Fix methods returning empty result set ( getPseudoColumns() etc) to have correct number and type of columns. Add tests to check correct structure of returned result sets. - Consistently map MySQL schemas to JDBC catalogs.
* [Revision #384](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/384)\
  Sat 2013-01-12 00:18:40 +0100
  * [CONJ-12](https://jira.mariadb.org/browse/CONJ-12) - support dumpQueriesOnException=true in JDBC URL. Also dump queries on syntax errors.
* [Revision #383](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/383)\
  Tue 2013-01-08 01:48:38 +0100
  * Fix asserton that is thrown if Connection.getWarnings() called after connection is closed. (observed when using Netbeans with the driver)
  * Also, add check for closed connection before statements execution.
* [Revision #382](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/382)\
  Tue 2013-01-08 01:32:55 +0100
  * [CONJ-8](https://jira.mariadb.org/browse/CONJ-8) - fix MySQLDatabaseMetaData ConnectorJ compatibility wrt schemas vs catalogs ,i.e make supportsSchemasXXX methods return false, and supportsCatalogsXXXX return true.
* [Revision #381](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/381)\
  Mon 2013-01-07 01:36:34 +0100
  * remove common database metadata. move methods to MySQLDatabaseMetaData. This abstraction was only useful to support drizzle server, and now got obsolete
* [Revision #380](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/380)\
  Sun 2013-01-06 01:24:23 +0100
  * Build : compile for Java6. remove unused dependency on mockito
* [Revision #379](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/379)\
  Sun 2013-01-06 01:22:56 +0100
  * [CONJ-7](https://jira.mariadb.org/browse/CONJ-7) : support IPv6 addresses in JDBC URL (square-bracket syntax)
* [Revision #378](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/378)\
  Fri 2013-01-04 12:12:00 +0100
  * Fix test case
* [Revision #377](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/377)\
  Fri 2013-01-04 12:11:46 +0100
  * Fix warnings about unused variables
* [Revision #376](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/376)\
  Fri 2013-01-04 12:11:00 +0100
  * [CONJ-1](https://jira.mariadb.org/browse/CONJ-1) : use a single (static) java.util.Timer and multiple TimerTasks to implement timeouts, rather than multiple Timers, since every java.util.Timer has a background thread attached to it.
* [Revision #375](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/375)\
  Tue 2012-12-25 16:38:29 +0100
  * support dumpQueriesOnException=true in the JDBC URL.
* [Revision #374](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/374)\
  Fri 2012-12-21 19:15:36 +0100
  * remove 'All rights reserved' from the copyright notice
* [Revision #373](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/373)\
  Thu 2012-12-20 17:57:38 +0100
  * simplify Statement.close
* [Revision #372](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/372)\
  Sun 2012-12-16 00:39:35 +0100
  * [CONJ-1](https://jira.mariadb.org/browse/CONJ-1) - Timeout behavior is erratic. The actual reason is bug in socket timeout implementation in the JVM (at least reproducible on Windows), that manifests in following socket behavior - once timeout on a socket occurs, after this the socket is "hosed" - after it, any timeout > 0 will result to immediate SocketTimeoutException. To workaround, timeout is reimplemented again, with the Timer. The implementation is moved from Protocol to Statement impementation , where it belongs to.
* [Revision #371](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/371)\
  Sat 2012-12-15 23:30:12 +0100
  * [CONJ-1](https://jira.mariadb.org/browse/CONJ-1) - Extend test case to reproduce erratic behavior of socket based query timeout.
* [Revision #370](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/370)\
  Mon 2012-12-10 15:51:17 +0100
  * support sessionVariables connection URL parameter
* [Revision #369](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/369)\
  Sun 2012-12-09 17:40:13 +0100
  * Fix warnings - unused class members, variables. Ensure all enum values are handled in switch statements
* [Revision #368](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/368)\
  Sun 2012-12-09 17:38:48 +0100
  * Accept "jdbc:mariadb:" prefix in addition to "jdbc:mysql", simplify url parsing code
* [Revision #367](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/367)\
  Sun 2012-12-09 17:35:37 +0100
  * Cleanup, fix eclipse warnings - add serialVersion field to all serializable classes.
* [Revision #366](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/366)\
  Sun 2012-12-09 17:31:53 +0100
  * [MDEV-3919](https://jira.mariadb.org/browse/MDEV-3919) : generate custom MANIFEST.MF to satisfy OSGi rules
* [Revision #365](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/365)\
  Wed 2012-12-05 17:31:38 +0100
  * [MDEV-3916](https://jira.mariadb.org/browse/MDEV-3916) : ArrayOutOffBounds exception parsing JDBC URL
  * Fix parsing parameters , contributed by Bjorn Melinder.
* [Revision #364](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/364)\
  Mon 2012-12-03 14:32:49 +0100
  * Change version (test buildbot)
* [Revision #363](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/363)\
  Sun 2012-12-02 03:21:39 +0100
  * remove drizzle related time packing routines, remove checking for Java5. This driver does not work with java5
* [Revision #362](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/362)\
  Sun 2012-12-02 02:51:00 +0100
  * refactor callable statement tests
* [Revision #361](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/361)\
  Sun 2012-12-02 02:11:38 +0100
  * test refactoring, do not strip comments from prepared statements
* [Revision #360](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/360)\
  Sat 2012-12-01 22:48:25 +0100
  * remove unused method, cleanup escape processing test
* [Revision #359](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/359)\
  Sat 2012-12-01 19:01:12 +0100
  * test commit to check buildbot
* [Revision #358](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/358)\
  Sat 2012-12-01 18:34:50 +0100
  * test commit to check buildbot
* [Revision #357](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/357)\
  Fri 2012-11-30 04:32:53 +0100
  * fix useSSL,add trustServerCertificate
* [Revision #356](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/356)\
  Fri 2012-11-30 03:09:01 +0100
  * copy with SSL sockets not supporting shutdownOutput
* [Revision #355](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/355)\
  Fri 2012-11-30 01:41:07 +0100
  * Support generic URLs in LOAD DATA LOCAL INFILE
* [Revision #354](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/354)\
  Thu 2012-11-29 21:13:35 +0100
  * Minor cleanup : remove unused stuff, fix comments
* [Revision #353](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/353)\
  Thu 2012-11-29 20:54:06 +0100
  * Remove comments, mostly IDE generated, but also wrong and trivial ones
* [Revision #352](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/352)\
  Thu 2012-11-29 20:39:10 +0100
  * More copyright dance. Remove SSL test, it does not do anything
* [Revision #351](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/351)\
  Thu 2012-11-29 18:48:23 +0100
  * copyright dance
* [Revision #350](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/350)\
  Thu 2012-11-29 17:29:19 +0100
  * fix license, project name etc in pom.xml
* [Revision #349](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/349)\
  Thu 2012-11-29 15:56:32 +0100
  * Fixed typo. Thanks to Mark Leith for this contribution
* [Revision #348](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/348)\
  Thu 2012-11-29 15:49:14 +0100
  * Fix typo.
  * Thanks Mark Leith for this contribution.
* [Revision #347](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/347)\
  Thu 2012-11-29 00:44:51 +0100
  * rebranding driver

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
