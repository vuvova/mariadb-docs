# MariaDB Connector/J 1.3.4 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/1.3.4/)[Release Notes](../../1.3/mariadb-connector-j-134-release-notes.md)[Changelog](mariadb-connector-j-134-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 12 Jan 2016

For the highlights of this release, see the [release notes](../../1.3/mariadb-connector-j-134-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more details of the revision and view diffs of the code modified in that revision.

## Major

* [CONJ-242](https://jira.mariadb.org/browse/CONJ-242) : Support client keystore and/or server truststore configuration.
  * [Revision #e1803fa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e1803fa) 2015-11-17
  * [Revision #e1803fa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e1803fa) 2015-11-17
  * [Revision #e1803fa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e1803fa) 2015-11-17
  * [Revision #e1803fa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e1803fa) 2015-11-17
* [CONJ-238](https://jira.mariadb.org/browse/CONJ-238) : PrepareStatement prepare exception handling [Revision #8cb011c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8cb011c) 2015-12-31
* [CONJ-236](https://jira.mariadb.org/browse/CONJ-236) : Correction on using getInt on a signed smallInt negative value on prepareStatement [Revision #88c9f30](https://github.com/mariadb-corporation/mariadb-connector-j/commit/88c9f30) 2015-12-26
* Failover improvement
  * Fix race conditions around static 'blacklist' map : [Revision #06494a7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/06494a7) 2015-12-11
  * Switch from System.currentTimeMillis() to System.nanoTime() to avoid System timeclock dependency : [Revision #ce36085](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ce36085) 2015-12-11
  * [Revision #e3900fa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e3900fa) 2015-12-15
  * [Revision #e9a08c5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e9a08c5) 2015-12-17
  * [Revision #8c5bc3d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8c5bc3d) 2015-12-21
  * [Revision #b9d44be](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b9d44be) 2015-12-22
  * [Revision #bcfbc87](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bcfbc87) 2015-12-27
  * [Revision #90a992f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/90a992f) 2015-12-30
  * [Revision #1473524](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1473524) 2015-12-30
  * [Revision #cf3ba64](https://github.com/mariadb-corporation/mariadb-connector-j/commit/cf3ba64) 2016-01-04
  * [Revision #36e8519](https://github.com/mariadb-corporation/mariadb-connector-j/commit/36e8519) 2016-01-05
  * [Revision #93a9461](https://github.com/mariadb-corporation/mariadb-connector-j/commit/93a9461) 2016-01-06
  * [Revision #07bf7b1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/07bf7b1) 2016-01-07
  * [Revision #655c830](https://github.com/mariadb-corporation/mariadb-connector-j/commit/655c830) 2016-01-07
  * [Revision #003d31d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/003d31d) 2016-01-07
  * [Revision #fb76158](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fb76158) 2016-01-07
  * [Revision #58962cc](https://github.com/mariadb-corporation/mariadb-connector-j/commit/58962cc) 2016-01-08
  * [Revision #cf49a19](https://github.com/mariadb-corporation/mariadb-connector-j/commit/cf49a19) 2016-01-08

## Fixes

* [CONJ-237](https://jira.mariadb.org/browse/CONJ-237) : Closing a close statement does not throw an Exception anymore. [Revision #4a949d2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4a949d2) 2015-12-26
* [CONJ-239](https://jira.mariadb.org/browse/CONJ-239) : Permit commit when in autocommit mode [Revision #6d156a1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6d156a1) 2016-01-09
* [CONJ-240](https://jira.mariadb.org/browse/CONJ-240) : Permit using Connection.setReadOnly(true) during a transaction mode [Revision #6d156a1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6d156a1) 2016-01-09

## Misc

* documentation :
  * [Revision #a473ad0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a473ad0) 2015-12-31
  * [Revision #634a781](https://github.com/mariadb-corporation/mariadb-connector-j/commit/634a781) 2015-12-31
  * [Revision #5baef6e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5baef6e) 2015-12-31
  * [Revision #939e92d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/939e92d) 2015-12-31
  * [Revision #7eb1e82](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7eb1e82) 2016-01-08
* test correction :
  * [Revision #7ef57d3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7ef57d3) 2015-12-15
  * [Revision #e0cd71a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e0cd71a) 2015-12-15
  * [Revision #008c6e7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/008c6e7) 2015-12-26

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
