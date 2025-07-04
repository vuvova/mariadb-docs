# MariaDB Java Client 1.1.3 Changelog

The most recent [_**Stable**_](../../../../mariadb-release-criteria.md) _**(GA)**_ release of [MariaDB Connector/J](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md) is:[**MariaDB Connector/J 3.5.3**](../../mariadb-connector-j-3-5-release-notes/mariadb-connector-j-3-5-3-release-notes.md)

[Download](https://downloads.mariadb.org/client-java/1.1.3/) | [Release Notes](../../mariadb-connector-j-11-release-notes/mariadb-java-client-113-release-notes.md) | **Changelog** |[Java Client Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-the-mariadb-java-client/README.md)

**Release date:** 1 Jul 2013

For the highlights of this release, see the [release notes](../../mariadb-connector-j-11-release-notes/mariadb-java-client-113-release-notes.md).

The revision number links will take you to the revision's page on Launchpad. On\
Launchpad you can view more details of the revision and view diffs of the code\
modified in that revision.

* [Revision #454](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/454)\
  Fri 2013-06-28 13:48:36 +0200
  * bump version
* [Revision #453](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/453)\
  Wed 2013-06-26 20:31:08 +0200
  * Remove useless long test
* [Revision #452](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/452)\
  Wed 2013-06-26 19:28:12 +0200
  * Remove @Override annotation for JDK7 methods (make Eclipse happy)
* [Revision #451](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/451)\
  Wed 2013-06-26 18:19:42 +0200
  * Fix tests (SSL detection)
* [Revision #450](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/450)\
  Wed 2013-06-26 18:00:55 +0200
  * Make compilable under by JDK7 - add missing methods for MySQLServerSidePreparedStatement
* [Revision #449](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/449)\
  Tue 2013-06-25 23:46:55 +0200
  * [CONJ-48](https://jira.mariadb.org/browse/CONJ-48): Introduce new parameters serverSslCert, which allows validation for self-signed server certificates.
  * Server certificate (or server CA certificate) can be passed in 3 forms
  * sslServerCert=/path/to/cert.pem (path to certificate) sslServerCert=classpath:relative/path (path relative to the current classpath) or as string, `sslServerCert=----BEGIN CERTIFICATE-----` ..
  * The certificate needs to be DER encoded, i.e it needs to start with `---BEGIN CERTIFICATE-----` line followed by base64 data, and end with `-----END CERTIFICATE-----`
  * Large part of this functionality was contributed by Sehrope Sarkuni.
* [Revision #448](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/448)\
  Sat 2013-06-22 21:53:04 +0200
  * [CONJ-47](https://jira.mariadb.org/browse/CONJ-47) : Fix executeBatch() methods to throw BatchUpdateException(), as per documentation.
  * Also, cleanup and simplify batch handling, remove complexity introduced with handler/ factory abstractions.
* [Revision #447](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/447)\
  Mon 2013-06-17 10:29:25 +0200
  * [CONJ-45](https://jira.mariadb.org/browse/CONJ-45): JDBC types in metadata for FLOAT and INT UNSIGNED are different than in ConnectorJ
  * Fix ResultSetMetaData.getColumnType() to be more ConnectorJ compatible `(FLOAT=>java.sql.Type.REAL`, rather than `java.sql.Type.FLOAT etc)`
  * Patch by Davy Verstappen.
* [Revision #446](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/446)\
  Sun 2013-06-16 22:53:24 +0200
  * fix build
* [Revision #445](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/445)\
  Sat 2013-06-15 00:06:09 +0200
  * [CONJ-44](https://jira.mariadb.org/browse/CONJ-44) : Fix bug in prepared statement parsing code (skipping next character after backslash '')
* [Revision #444](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/444)\
  Fri 2013-06-14 15:22:27 +0200
  * remove dummy test
* [Revision #443](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/443)\
  Fri 2013-06-14 15:00:20 +0200
  * fix ResultSet.getDisplaySize() for character columns - due to UTF-8 usage it was 3x more than expected
* [Revision #442](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/442)\
  Fri 2013-06-14 14:58:19 +0200
  * [CONJ-35](https://jira.mariadb.org/browse/CONJ-35) : provide alternative implementation for `DatabaseMetadata.getImportedKeys()` that does not use information schema, but parses the output of "show create table" instead.
  * The reason for it is to speed up `DatabaseMetadata.getImportedKeys()` call , which can get very slow in certain scenarios involving hibernate
* [Revision #441](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/441)\
  Tue 2013-06-11 16:25:04 +0200
  * update version of surefire plugin in pom.xml, to be able to run single test
* [Revision #440](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/440)\
  Tue 2013-06-11 16:22:59 +0200
  * [CONJ-41](https://jira.mariadb.org/browse/CONJ-41) : `DatabaseMetaData.getPrimaryKeys` returns incorrect value for `KEY_SEQ` (`ORDINAL_POSITION` from `INFORMATION_SCHEMA.COLUMNS` is incorrectly returned)
  * The fix to join `I_S.COLUMNS` with `I_S.STATISTICS` and to use `INFORMATION_SCHEMA.STATISTICS.SEQ_IN_INDEX` for `KEY_SEQ`.
* [Revision #439](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/439)\
  Fri 2013-06-07 18:57:11 +0200
  * [CONJ-40](https://jira.mariadb.org/browse/CONJ-40) : allow `java.util.Date` to be passed to `PreparedStatement.setObject()`
* [Revision #438](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/438)\
  Fri 2013-06-07 17:18:58 +0200
  * [CONJ-43](https://jira.mariadb.org/browse/CONJ-43) : An exception is thrown when using `PreparedStatement.getResultSetMetaData()`, prior to statement execution. Statement must contain at least one '?' placeholder to trigger the exception
  * The reason for the bug was incorrect reading of `COM_STMT_PREPARE` response in this case (wrong order of parameter definition block and column definition block)
* [Revision #437](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/437)\
  Tue 2013-05-28 10:35:24 +0200
  * [CONJ-39](https://jira.mariadb.org/browse/CONJ-39) : multi-row inserts should return multiple entries in `getGeneratedKeys()`
* [Revision #436](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/436)\
  Tue 2013-05-28 09:53:41 +0200
  * [CONJ-42](https://jira.mariadb.org/browse/CONJ-42) - Escape processing - allow for missing space it temporal escapes, for better compatibility with ConnectorJ
* [Revision #435](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/435)\
  Thu 2013-05-23 22:18:40 +0200
  * [CONJ-39](https://jira.mariadb.org/browse/CONJ-39) : for multi-row inserts, `getGeneratedKeys()` will return ResultSet with multiple entries. like ConnectorJ does.
* [Revision #434](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/434)\
  Wed 2013-05-22 00:04:43 +0200
  * [CONJ-38](https://jira.mariadb.org/browse/CONJ-38) - Fix threading issue in `MySQLCallableStatement`.
  * 3 operations - setting input parameters, caling stored procedure and reading off the output parameters must be "atomic". i.e it needs to be synchronized so that it does not interfere with other clients using the same Connection in a different thread.
* [Revision #433](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/433)\
  Tue 2013-05-21 13:55:57 +0200
  * CONJ37- don't connect socket if it is already connected - (i.e in case custom SocketFactory creates an already connected sockets)
* [Revision #432](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/432)\
  Thu 2013-05-09 13:45:22 +0200
  * fix named pipe remote access
* [Revision #431](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/431)\
  Tue 2013-05-07 23:02:02 +0200
  * [CONJ-36](https://jira.mariadb.org/browse/CONJ-36) : implement connections via named pipe on Windows (via pipe= syntax in the connect URL)
* [Revision #430](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/430)\
  Mon 2013-05-06 20:42:09 +0200
  * [CONJ-34](https://jira.mariadb.org/browse/CONJ-34) : Change assertion in PacketOutputStream.startPacket() to be IOException (so it can be caught). "Last packet not finished" condition can happen , if underlying stream is broken (e.g write operation failed)
* [Revision #429](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/429)\
  Fri 2013-05-03 00:05:34 +0200
  * Add build script to bazaar repository
* [Revision #428](https://bazaar.launchpad.net/~maria-captains/mariadb-java-client/trunk/revision/428)\
  Fri 2013-05-03 00:04:52 +0200
  * MySQLProtocol has this like in executeQuery :
  * log.finest("Executing streamed query: " + dQuery);
  * Even if log is not activated (which is normally the case), even then relatively expensive string concatenation takes place.It should be avoided by using
  * `log.log(Level.FINEST, "Executing streamed query: {0}", dQuery);`
  * instead.

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
