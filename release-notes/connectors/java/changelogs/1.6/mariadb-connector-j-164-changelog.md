# MariaDB Connector/J 1.6.4 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/1.6.4/)[Release Notes](../../1.6/mariadb-connector-j-164-release-notes.md)[Changelog](mariadb-connector-j-164-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 6 Sep 2017

For the highlights of this release, see the [release notes](../../1.6/mariadb-connector-j-164-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #4e0b97ef](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4e0b97ef) - \[misc] add developers information's since needed for sonatype
* [Revision #9acdeece](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9acdeece) - bump 1.6.4 version
* [Revision #a5b2f3e8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a5b2f3e8) - \[misc] remove unused access of @@sql\_mode during connection time
* [Revision #abba3989](https://github.com/mariadb-corporation/mariadb-connector-j/commit/abba3989) - \[misc] initialize read-ahead scheduler only if needed
* [Revision #348d294f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/348d294f) - \[misc] avoid Unix domain socket multiple close and java code cleaning
* [Revision #b8551cee](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b8551cee) - \[misc] improving option "enablePacketDebug"
* [Revision #ff8f116f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ff8f116f) - \[misc] correction of possible race condition when multi threading on result set with fetch
* [Revision #804871ba](https://github.com/mariadb-corporation/mariadb-connector-j/commit/804871ba) - \[[CONJ-514](https://jira.mariadb.org/browse/CONJ-514)] ResultSet method wasNull() always return true after a call on a "null-date" field binary protocol handling
* [Revision #b3915fd7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b3915fd7) - \[[CONJ-514](https://jira.mariadb.org/browse/CONJ-514)] ResultSet method wasNull() always return true after a call on a "null-date" field ("0000-00-00 00:00:00" for timestamp, "0000-00-00" for date , ...)
* [Revision #9488fafe](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9488fafe) - \[misc] correcting debug output when having offset
* [Revision #43da82e8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/43da82e8) - \[[CONJ-517](https://jira.mariadb.org/browse/CONJ-517)] correcting result-set identification of OK\_Packet with 0xFE header when using option useCompression
* [Revision #f91a9727](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f91a9727) - \[misc] remove test that is effective 99% of the time (performance test) for better CI reliability
* [Revision #8239945f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8239945f) - \[misc] checkstyle correction
* [Revision #89c1895f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/89c1895f) - bump 1.6.4-SNAPSHOT version
* [Revision #2beeacdb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2beeacdb) - \[[CONJ-515](https://jira.mariadb.org/browse/CONJ-515)] Improve MariaDB driver stability in case JNA errors from @oleg-alexeyev : [110](https://github.com/MariaDB/mariadb-connector-j/pull/110)
* [Revision #aa65429d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/aa65429d) - \[misc] failover loop correction
* [Revision #6d854f47](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6d854f47) - \[misc] improve error message on setting erroneous parameter
* [Revision #ca1cae5a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ca1cae5a) - \[misc] delete inaccurate list of developers in pom

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
