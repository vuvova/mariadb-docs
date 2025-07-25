# Connector/ODBC 3.1.20 Changelog

The most recent [_**Stable**_](../../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/ODBC is:[**MariaDB Connector/ODBC 3.2.5**](../../mariadb-connector-odbc-3-2-release-notes/mariadb-connector-odbc-3-2-5-release-notes.md)

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/odbc-connector)[Release Notes](../../mariadb-connector-odbc-3-1-release-notes/mariadb-connector-odbc-3-1-20-release-notes.md)[Changelog](mariadb-connector-odbc-3-1-20-changelog.md)[About MariaDB Connector/ODBC](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-odbc/README.md)

**Release date:** 4 Dec 2023

For the highlights of this release, see the [release notes](../../mariadb-connector-odbc-3-1-release-notes/mariadb-connector-odbc-3-1-20-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-odbc) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #9241fb8](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/9241fb8)\
  2023-12-01 11:15:36 +0100
  * Fix of SQLCanclel testcase, that would fail in case of RS streaming
* [Revision #cdb2990](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/cdb2990)\
  2023-11-30 21:04:58 +0100
  * [ODBC-399](https://jira.mariadb.org/browse/ODBC-399) Error on the query consisting from the comment only
* [Revision #9b117a1](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/9b117a1)\
  2023-11-30 14:39:27 +0100
  * [ODBC-404](https://jira.mariadb.org/browse/ODBC-404) Use SET STATEMENT only with servers, that support it
* [Revision #5ef91f2](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/5ef91f2)\
  2023-11-29 12:28:46 +0100
  * libmariadb submodule has been updated to v3.3.8
* [Revision #d99a261](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/d99a261)\
  2023-11-27 22:14:22 +0100
  * Fixes for MacOS/iOdbc
* [Revision #5f1fbdf](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/5f1fbdf)\
  2023-11-29 01:02:31 +0100
  * [ODBC-402](https://jira.mariadb.org/browse/ODBC-402) Support of NO\_BIGINT option with testcase
* [Revision #014e86b](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/014e86b)\
  2023-11-22 17:30:10 +0100
  * [ODBC-399](https://jira.mariadb.org/browse/ODBC-399) The testcase, as it appears now
* [Revision #314a1c2](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/314a1c2)\
  2023-11-22 10:43:04 +0100
  * [ODBC-401](https://jira.mariadb.org/browse/ODBC-401) SQLCancel fix
* [Revision #41b9d83](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/41b9d83)\
  2023-10-30 12:35:35 +0100
  * Small improvement in the connection process
* [Revision #349fe3b](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/349fe3b)\
  2023-09-22 00:23:38 +0200
  * Changes in tests for xpand
* [Revision #790b58b](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/790b58b)\
  2023-08-07 11:11:03 +0530
  * Fix Travis build for s390x
* [Revision #1598057](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/1598057)\
  2023-09-20 15:12:36 +0200
  * Removing dependency on pkg-config from binary rpm
* [Revision #77102f7](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/77102f7)\
  2023-09-18 12:36:56 +0200
  * C/C submodule has been updated to v3.3.7 release tag
* [Revision #0be3743](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/0be3743)\
  2023-09-05 22:23:38 +0200
  * Added dependencies to source rpm
* [Revision #86ad76e](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/86ad76e)\
  2023-08-30 16:00:21 +0200
  * Added 23.08 to travis matrix
* [Revision #c78d08f](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/c78d08f)\
  2023-08-23 13:49:39 +0200
  * Adding dirver UnixODBC template ini file to installation(RPM/DEB/TGZ)
* [Revision #9209023](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/9209023)\
  2023-08-13 23:10:32 +0200
  * Fix of travis script
* [Revision #bbe48ab](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/bbe48ab)\
  2023-07-21 00:24:43 +0200
  * Fix of couple of tests for the case of resultset streaming
* [Revision #abb23df](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/abb23df)\
  2023-07-20 17:18:43 +0200
  * [ODBC-395](https://jira.mariadb.org/browse/ODBC-395) The fix and the testcase
* [Revision #a7ba72d](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/a7ba72d)\
  2023-07-20 15:24:12 +0200
  * [ODBC-394](https://jira.mariadb.org/browse/ODBC-394) Changed use of tx\_isolation to transaction\_isolation
* [Revision #97b6d5e](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/97b6d5e)\
  2023-07-07 14:35:59 -0400
  * bump the VERSION

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
