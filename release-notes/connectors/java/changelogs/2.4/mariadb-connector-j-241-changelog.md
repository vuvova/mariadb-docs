# MariaDB Connector/J 2.4.1 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.com/Connectors/java/connector-java-2.4.1/)[Release Notes](../../2.4/mariadb-connector-j-241-release-notes.md)[Changelog](mariadb-connector-j-241-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 18 Mar 2019

For the highlights of this release, see the [release notes](../../2.4/mariadb-connector-j-241-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #7c2220f3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7c2220f3) - bump version 2.4.1
* [Revision #974c9642](https://github.com/mariadb-corporation/mariadb-connector-j/commit/974c9642) - \[misc] updating checkstyle version dependency
* [Revision #d44da9bd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d44da9bd) - \[misc] permit using SSL on localsocket
* [Revision #b195649d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b195649d) - \[misc] update appveyor test to last released version
* [Revision #7cd4b675](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7cd4b675) - \[misc] added error code 1213 to a list for running INNODB STATUS query - changed array + Stream with Set + contains approach for checking codes
* [Revision #c4172f22](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c4172f22) - \[[CONJ-687](https://jira.mariadb.org/browse/CONJ-687)] travis test correction for option "useMysqlMetadata" with AURORA
* [Revision #42183c05](https://github.com/mariadb-corporation/mariadb-connector-j/commit/42183c05) - \[[CONJ-687](https://jira.mariadb.org/browse/CONJ-687)] addition of option "useMysqlMetadata" to permit MySQL meta compatibility
* [Revision #ec86522f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ec86522f) - Change the query to fetch innodb\_read\_only from SHOW GLOBAL VARIABLES into SELECT to reduce mutex contention
* [Revision #09a92c96](https://github.com/mariadb-corporation/mariadb-connector-j/commit/09a92c96) - \[misc] java PID using java 9 ProcessHandle if existing, relying on JNA if present
* [Revision #a5896ee8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a5896ee8) - \[misc] changing test for 10.4 compatibility
* [Revision #b7a99324](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b7a99324) - \[[CONJ-682](https://jira.mariadb.org/browse/CONJ-682)] internal pool correction: when receiving an RST during connection validation, the pool will end up throwing connection timeout exception in place of reusing another connection.
* [Revision #bc985a83](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bc985a83) - \[misc] added error code 1213 to a list for running INNODB STATUS query - 1213 ER\_LOCK\_DEADLOCK was not considered to run 'SHOW ENGINE INNODB STATUS'
* [Revision #74e7f96d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/74e7f96d) - Update README.md

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
