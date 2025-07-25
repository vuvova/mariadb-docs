# Connector/C 2.3.3 Changelog

The most recent [_**Stable**_](../../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/C is:[**MariaDB Connector/C 3.4.5**](../../mariadb-connector-c-3-4-release-notes/mariadb-connector-c-3-4-5-release-notes.md)

[Download](https://downloads.mariadb.org/connector-c/2.3.3)[Release Notes](../../mariadb-connector-c-23-release-notes/mariadb-connector-c-233-release-notes.md)[Changelog](mariadb-connector-c-233-changelog.md)[About MariaDB Connector/C](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-c/README.md)

**Release date:** 31 May 2017

For the highlights of this release, see the [release notes](../../mariadb-connector-c-23-release-notes/mariadb-connector-c-233-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-c/) you can view more details of the revision and view diffs of the code\
modified in that revision.

* [Revision #42d6d3f](https://github.com/mariadb-corporation/mariadb-connector-c/commit/42d6d3f)\
  2017-05-18 13:07:16 +0200
  * timeout values, which are "unsigned int" in both the connector API and the underlying sockets API, transit at some point into signed int and are assigned the value "-1" whenever the timeout is not defined. The resulting socket timeout being computed based on the conversion of -1 to an unsigned int, instead of being "0" (no socket timeout). Kudos to Nicolas Leroux for providing the patch.
* [Revision #633109c](https://github.com/mariadb-corporation/mariadb-connector-c/commit/633109c)\
  2017-03-22 05:33:29 +0100
  * Fix parameter type for parameter reconnect in mysql\_optionsv from uint to my\_bool
* [Revision #30614c7](https://github.com/mariadb-corporation/mariadb-connector-c/commit/30614c7)\
  2017-02-05 12:00:25 +0100
  * Fix for [CONC-231](https://jira.mariadb.org/browse/CONC-231): Wrong FSF address
* [Revision #8b36952](https://github.com/mariadb-corporation/mariadb-connector-c/commit/8b36952)\
  2017-01-30 18:04:06 +0100
  * Fixed error check for timeout on sockets (poll)
* [Revision #e714cf4](https://github.com/mariadb-corporation/mariadb-connector-c/commit/e714cf4)\
  2017-01-21 18:36:11 +0100
  * Removed unnecessary dependency of mariadbclientlib
* [Revision #025d912](https://github.com/mariadb-corporation/mariadb-connector-c/commit/025d912)\
  2017-01-20 19:27:51 +0100
  * Fix for [CONC-226](https://jira.mariadb.org/browse/CONC-226): Build fails on big-endian platforms - merge from C/C 3.0 ([MDEV-10894](https://jira.mariadb.org/browse/MDEV-10894)) was incomplete
* [Revision #542a146](https://github.com/mariadb-corporation/mariadb-connector-c/commit/542a146)\
  2017-01-20 19:24:44 +0100
  * Bumped version number

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
