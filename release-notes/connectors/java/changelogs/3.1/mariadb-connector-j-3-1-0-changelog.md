# MariaDB Connector/J 3.1.0 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](../../3.1/mariadb-connector-j-3-1-0-release-notes.md)[Changelog](mariadb-connector-j-3-1-0-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 15 Nov 2022

For the highlights of this release, see the [release notes](../../3.1/mariadb-connector-j-3-1-0-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #9a04ccc9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9a04ccc9) - Merge tag '3.1.0' into develop
* [Revision #931f45e9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/931f45e9) - Merge branch 'release/3.1.0'
* [Revision #8216832a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8216832a) - bump 3.1.0 version
* [Revision #db68d085](https://github.com/mariadb-corporation/mariadb-connector-j/commit/db68d085) - \[misc] 3.0.9 merge
* [Revision #a0a442ea](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a0a442ea) - Merge branch 'release/3.0.9' into develop
* [Revision #87f6b918](https://github.com/mariadb-corporation/mariadb-connector-j/commit/87f6b918) - \[misc] test reliability improvement when using maxscale
* [Revision #291971dc](https://github.com/mariadb-corporation/mariadb-connector-j/commit/291971dc) - \[misc] bump POM dependencies JVM config is needed for [99](https://github.com/spotify/fmt-maven-plugin/issues/99) / [787](https://github.com/google/google-java-format/issues/787)
* [Revision #d31e6726](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d31e6726) - \[[CONJ-899](https://jira.mariadb.org/browse/CONJ-899)] Support UUID Object
* [Revision #a55fa423](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a55fa423) - \[misc] code style correction
* [Revision #c105aa0b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c105aa0b) - Merge branch 'release/3.0.9' into develop
* [Revision #7a6617ed](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7a6617ed) - \[[CONJ-1021](https://jira.mariadb.org/browse/CONJ-1021)] add windows GSSAPI test
* [Revision #5ac67b2d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5ac67b2d) - \[[CONJ-1021](https://jira.mariadb.org/browse/CONJ-1021)] enable waffle dependency for better Windows GSSAPI use
* [Revision #34eff1c3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/34eff1c3) - \[misc] code style correction
* [Revision #9c6135a3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9c6135a3) - \[[CONJ-1021](https://jira.mariadb.org/browse/CONJ-1021)] GSSAPI authentication might result in connection reset
* [Revision #48e5534a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/48e5534a) - \[misc] skip test with `FLUSH PRIVILEGES` with MySQL server 8.0.31 that broke server public key retrieval afterwhile
* [Revision #ea5aa216](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ea5aa216) - \[[CONJ-1019](https://jira.mariadb.org/browse/CONJ-1019)] DatabaseMetaData.getImportedKeys should return real value for PK\_NAME column
* [Revision #7300dc9f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7300dc9f) - \[[CONJ-1020](https://jira.mariadb.org/browse/CONJ-1020)] correcting java 11+ socket options setting
* [Revision #0fbe8921](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0fbe8921) - \[[CONJ-992](https://jira.mariadb.org/browse/CONJ-992)] load balance distribution now use round robin, ensuring better distribution than previous random order
* [Revision #d6fa61bd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d6fa61bd) - \[[CONJ-916](https://jira.mariadb.org/browse/CONJ-916)] when a failover occurs, log replayed transaction
* [Revision #e4be6894](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e4be6894) - \[[CONJ-917](https://jira.mariadb.org/browse/CONJ-917)] deprecated option are now logger when logger is enabled
* [Revision #be365e0d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/be365e0d) - \[misc] add maxscale log when failing
* [Revision #2bf55027](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2bf55027) - \[misc] ascii encoding improvement
* [Revision #2ca2b891](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2ca2b891) - \[misc] code style correction
* [Revision #aeb9fd4f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/aeb9fd4f) - \[misc] ensuring test reliability
* [Revision #1ff230f7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1ff230f7) - \[[CONJ-1017](https://jira.mariadb.org/browse/CONJ-1017)] concurrent data/time/timestamp when using same calendar parameter missing synchronization
* [Revision #7586df89](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7586df89) - \[misc] ensure client prepare statement lock when closing bulk
* [Revision #36a10598](https://github.com/mariadb-corporation/mariadb-connector-j/commit/36a10598) - \[[CONJ-1016](https://jira.mariadb.org/browse/CONJ-1016)] avoid splitting BULK command into multiple commands in case of prepareStatement.setNull() use
* [Revision #fc1eb31d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fc1eb31d) - \[misc] javadoc correction
* [Revision #3aa6c143](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3aa6c143) - \[[CONJ-1009](https://jira.mariadb.org/browse/CONJ-1009)] creating missing javadoc
* [Revision #87d8673c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/87d8673c) - \[misc] bump 3.1.0 SNAPSHOT
* [Revision #eee5184a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/eee5184a) - \[[CONJ-1015](https://jira.mariadb.org/browse/CONJ-1015)] pipelining now write to socket only one array, permitting faster command execution when on distant server
* [Revision #072e4127](https://github.com/mariadb-corporation/mariadb-connector-j/commit/072e4127) - \[[CONJ-1014](https://jira.mariadb.org/browse/CONJ-1014)] avoid creating array when receiving server packet
* [Revision #0803f6d1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0803f6d1) - \[misc] server prepare statement ensuring command is preparable test improvement
* [Revision #d9d2254d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d9d2254d) - \[[CONJ-1013](https://jira.mariadb.org/browse/CONJ-1013)] Skip parsing parameter metadata since doesn't contains real information
* [Revision #6dd17abf](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6dd17abf) - \[misc] benchmark add binary command without pipeline
* [Revision #4e48559f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4e48559f) - \[misc] correct test suite after MySQL 8 sending erroneous MYSQL\_TYPE\_INVALID data type
* [Revision #dc503253](https://github.com/mariadb-corporation/mariadb-connector-j/commit/dc503253) - \[misc] add batch benchmark test
* [Revision #211e286e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/211e286e) - \[[CONJ-1009](https://jira.mariadb.org/browse/CONJ-1009)] improve performance reading result-set of big size part 3
* [Revision #22cff70d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/22cff70d) - \[[CONJ-1009](https://jira.mariadb.org/browse/CONJ-1009)] improve performance reading result-set of big size part 2
* [Revision #2df376a9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2df376a9) - \[[CONJ-1012](https://jira.mariadb.org/browse/CONJ-1012)] stored procedure register output parameter as null if set before registerOutParameter command
* [Revision #be5a76ec](https://github.com/mariadb-corporation/mariadb-connector-j/commit/be5a76ec) - \[[CONJ-1009](https://jira.mariadb.org/browse/CONJ-1009)] improve performance reading result-set of big size
* [Revision #6cf6d1bd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6cf6d1bd) - \[misc] fast path for unsigned long decoding
* [Revision #c2160bfa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c2160bfa) - Merge tag '3.0.8' into develop

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
