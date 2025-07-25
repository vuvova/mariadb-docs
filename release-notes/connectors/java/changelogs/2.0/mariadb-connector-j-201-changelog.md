# MariaDB Connector/J 2.0.1 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.0.1/)[Release Notes](../../2.0/mariadb-connector-j-201-release-notes.md)[Changelog](mariadb-connector-j-201-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 11 May 2017

For the highlights of this release, see the [release notes](../../2.0/mariadb-connector-j-201-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #d56ba5a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d56ba5a) - \[misc] bump 2.0.1 version
* [Revision #17db846](https://github.com/mariadb-corporation/mariadb-connector-j/commit/17db846) - \[misc] checkstyle correction
* [Revision #8a31453](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8a31453) - \[misc] changing default option value useServerPrepStmts to false (use text protocol by default)
* [Revision #1b99cda](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1b99cda) - \[misc] changing metadata to 4.2
* [Revision #d9ef3d0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d9ef3d0) - \[misc] temporary remove MARIADB\_CLIENT\_COM\_IN\_AUTH, waiting for server release
* [Revision #8ff2a57](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8ff2a57) - \[misc] javadoc correction
* [Revision #cac0dbd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/cac0dbd) - \[[CONJ-465](https://jira.mariadb.org/browse/CONJ-465)] new option "enablePacketDebug" Driver will save the last 16 MySQL packet exchanges (limited to first 1000 bytes). Hexadecimal value of those packet will be added to stacktrace when an IOException occur. This options has no performance incidence (< 1 microseconds per query) but driver will then take 16kb more memory.
* [Revision #dcb7fa4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/dcb7fa4) - \[misc] removing unused methods
* [Revision #a5b8187](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a5b8187) - \[[CONJ-464](https://jira.mariadb.org/browse/CONJ-464)] Using of "slowQueryThresholdNanos" option with value > Integer.MAX\_VALUE results in class cast exception
* [Revision #05891d1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/05891d1) - \[[CONJ-452](https://jira.mariadb.org/browse/CONJ-452)] correcting inline ssl server certificate parsing
* [Revision #a13a050](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a13a050) - \[misc] set socket timeout after connection
* [Revision #503dd4f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/503dd4f) - \[[CONJ-461](https://jira.mariadb.org/browse/CONJ-461)] LAST\_INSERT\_ID() validation check correction
* [Revision #e012977](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e012977) - \[misc] autoIncrementIncrement value loaded when connecting, avoiding a query for first statement
* [Revision #c25c3cf](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c25c3cf) - update github tag for maven central
* [Revision #04a2771](https://github.com/mariadb-corporation/mariadb-connector-j/commit/04a2771) - \[[CONJ-461](https://jira.mariadb.org/browse/CONJ-461)] queries with LAST\_INSERT\_ID() must not be rewritten
* [Revision #5a80688](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5a80688) - \[[CONJ-460](https://jira.mariadb.org/browse/CONJ-460)] Query that contain multiqueries with fetch and EOF deprecation failed
* [Revision #ab90e3b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ab90e3b) - \[misc] change version to 2.0.1

test improvements : [Revision #59abff4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/59abff4), [Revision #9accea6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9accea6), [Revision #1c27460](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1c27460), [Revision #17db846](https://github.com/mariadb-corporation/mariadb-connector-j/commit/17db846), [Revision #5e1293e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5e1293e), [Revision #152eab5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/152eab5), [Revision #13fc827](https://github.com/mariadb-corporation/mariadb-connector-j/commit/13fc827), [Revision #ef25102](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ef25102), [Revision #76256dc](https://github.com/mariadb-corporation/mariadb-connector-j/commit/76256dc), [Revision #e895995](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e895995), [Revision #c976c38](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c976c38)

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
