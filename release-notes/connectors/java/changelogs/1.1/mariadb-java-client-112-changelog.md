# Connector/J 1.1.2 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/client-java/1.1.2/) | [Release Notes](../../1.1/mariadb-java-client-112-release-notes.md) | **Changelog** |[Java Client Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-the-mariadb-java-client/README.md)

**Release date:** 02 May 2013

For the highlights of this release, see the [release notes](../../1.1/mariadb-java-client-112-release-notes.md).

The revision number links will take you to the revision's page on Launchpad. On\
Launchpad you can view more details of the revision and view diffs of the code\
modified in that revision.

* [Revision #426](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/426)\
  Wed 2013-05-01 16:20:40 +0200
  * 1.1.2 Release
* [Revision #425](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/425)\
  Wed 2013-05-01 16:07:38 +0200
  * Fix warnings
* [Revision #424](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/424)\
  Sun 2013-04-28 17:24:47 +0200
  * CONJ21- allow ResultSetMetaData to be retrieved from preparedStatement, before statement is executed.
  * Fix is using server-side prepared statement functionality - prepare command\
    will return result set metadata among other information. Introduce\
    MySQLServerSidePreparedStatement class, which in the future will be able to\
    provide full-featured PreparedStatement functionality, using server side\
    prepared statements internally.
* [Revision #423](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/423)\
  Tue 2013-04-09 12:46:14 +0200
  * [CONJ-32](https://jira.mariadb.org/browse/CONJ-32) : more comments on replication hack in [MariaDB 10.0](../../../../community-server/old-releases/release-notes-mariadb-10-0-series/changes-improvements-in-mariadb-10-0.md)
* [Revision #422](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/422)\
  Mon 2013-04-08 23:03:00 +0200
  * [CONJ-30](https://jira.mariadb.org/browse/CONJ-30) : optimize Connection.getAutoCommit() and Connection.setAutoCommit()
  * The problem : excessive amount "`select @@autocommit`" and\
    "`set @@autocommit`" calls - occurs with 3rd party libraries, such as\
    Hibernate
  * The fix : don't issue queries
    * SQL query is not necessary to track autocommit status, analyzing server\
      status flags sent with OK,EOF or ERROR packet suffices.
    * Also, setAutoCommit(flag) is now a no-iop, if parameter 'flag' is the\
      current value of `getAutoCommit()`.
* [Revision #421](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/421)\
  Thu 2013-04-04 18:59:30 +0200
  * Adding LICENSE file, LGPL2.1
* [Revision #420](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/420)\
  Tue 2013-04-02 23:21:54 +0200
  * [CONJ-32](https://jira.mariadb.org/browse/CONJ-32) : remove fake version prefix in [MariaDB 10.0](../../../../community-server/old-releases/release-notes-mariadb-10-0-series/changes-improvements-in-mariadb-10-0.md) .
  * Background on fake version prefix can be found here : [MDEV-4088](https://jira.mariadb.org/browse/MDEV-4088)
* [Revision #419](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/419)\
  Wed 2013-03-27 18:44:16 +0100
  * [CONJ-31](https://jira.mariadb.org/browse/CONJ-31) : fix several issues with Clob and\
    PreparedStatement.setCharacterStream()
    * non-ASCII characters can get lost,\
      if `PreparedStatement.setCharacterStream()` is used.
    * If `PreparedStatement.setClob()` was used, CLOB was sent to the server\
      using binary introducer (\_BINARY). This can potentially lead to wrongly\
      stored non-ASCII characters.
  * Small cleanups :
    * remove try/catch around code that can't throw exceptions in\
      MySQLPreparedStatement
    * move all tests related to Clobs, Blobs, and streams to BlobTest.java
  * Thanks to Rune Bremnes, who contributed parts of this patch.
* [Revision #418](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/418)\
  Wed 2013-03-27 12:57:14 +0100
  * Change `Blob.getBinaryStream()` to limit the returned stream\
    to `MySQLBlog.actualSize` length.
  * Thanks to Rune Bremnes for providing idea of the patch.
* [Revision #417](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/417)\
  Sat 2013-03-16 15:41:13 +0100
  * Add copyright header that was removed by mistake.
* [Revision #416](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/416)\
  Thu 2013-03-07 21:47:19 +0100
  * [CONJ-28](https://jira.mariadb.org/browse/CONJ-28) : CHAR BINARY or VARCHAR BINARY field are erronerously handled as\
    BINARY type. They should be treated as character, as BINARY only specified\
    collation (i.e sort order), but the column still contains strings not\
    blobs.
  * The patch fixes `MySQLColumnInformation.isBinary()` function to return\
    true only if character set is 63 - the binary pseudo-charset code
* [Revision #415](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/415)\
  Thu 2013-02-28 23:48:27 +0100
  * bump version

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
