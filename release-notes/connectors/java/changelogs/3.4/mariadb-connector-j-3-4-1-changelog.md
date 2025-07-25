# MariaDB Connector/J 3.4.1 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](../../3.4/mariadb-connector-j-3-4-1-release-notes.md)[Changelog](mariadb-connector-j-3-4-1-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 17 Jul 2024

For the highlights of this release, see the [release notes](../../3.4/mariadb-connector-j-3-4-1-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #6943884f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6943884f) - correct README format
* [Revision #889ccf63](https://github.com/mariadb-corporation/mariadb-connector-j/commit/889ccf63) - bump 3.4.1 version
* [Revision #f68447f1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f68447f1) - \[[CONJ-1189](https://jira.mariadb.org/browse/CONJ-1189)] XA START RESUME even with TMJOIN flag when using pinGlobalTxToPhysicalConnection option
* [Revision #c2904a96](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c2904a96) - \[misc] metadata DatabaseMeta.getExportedKeys() test correction
* [Revision #66a51df9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/66a51df9) - \[[CONJ-1180](https://jira.mariadb.org/browse/CONJ-1180)] improve DatabaseMeta.getExportedKeys() performances
* [Revision #45d8e6da](https://github.com/mariadb-corporation/mariadb-connector-j/commit/45d8e6da) - \[[CONJ-1189](https://jira.mariadb.org/browse/CONJ-1189)] support for pinGlobalTxToPhysicalConnection option
* [Revision #873dde72](https://github.com/mariadb-corporation/mariadb-connector-j/commit/873dde72) - \[misc] code style correction
* [Revision #308cbb50](https://github.com/mariadb-corporation/mariadb-connector-j/commit/308cbb50) - \[misc] test for failover improvement for reliability
* [Revision #279b9031](https://github.com/mariadb-corporation/mariadb-connector-j/commit/279b9031) - \[[CONJ-1178](https://jira.mariadb.org/browse/CONJ-1178)] adding PK\_NAME in getImportedKeys ORDER for reliability
* [Revision #9f2e872f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9f2e872f) - \[[CONJ-1178](https://jira.mariadb.org/browse/CONJ-1178)] getImportedKeys return different PK\_NAME value than getExportedKeys.
* [Revision #8c33569a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8c33569a) - \[[CONJ-1190](https://jira.mariadb.org/browse/CONJ-1190)] creating alias for MySQL connector option 'databaseTerm' for option 'useCatalogTerm'
* [Revision #bf1f74a8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bf1f74a8) - \[[CONJ-1188](https://jira.mariadb.org/browse/CONJ-1188)] database meta getSQLKeywords listing all reserved key word, not restricted keywords only
* [Revision #3a81564d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3a81564d) - \[misc] javadoc improvement
* [Revision #6cdb75b8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6cdb75b8) - \[misc] update nexus-staging-maven-plugin version
* [Revision #8aa08926](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8aa08926) - \[misc] test improvement for MariaDB server 11.4.1+
* [Revision #1bdb0b38](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1bdb0b38) - \[[CONJ-1182](https://jira.mariadb.org/browse/CONJ-1182)] missing XA error mapping
* [Revision #e3158e48](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e3158e48) - \[[CONJ-1181](https://jira.mariadb.org/browse/CONJ-1181)] ensure prepare statement cache reliability when using multiple database
* [Revision #164e3a46](https://github.com/mariadb-corporation/mariadb-connector-j/commit/164e3a46) - \[test] ensure java 8 compatibility
* [Revision #53145a7c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/53145a7c) - \[test] ensure HostAddress data cannot be changed
* [Revision #24dd582c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/24dd582c) - \[test] test correction
* [Revision #e8349a80](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e8349a80) - \[[CONJ-685](https://jira.mariadb.org/browse/CONJ-685)] permit setting sslMode per host
* [Revision #eca13e7f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/eca13e7f) - \[[CONJ-686](https://jira.mariadb.org/browse/CONJ-686)] permit setting pipe and local socket per host
* [Revision #9330b44a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9330b44a) - \[[CONJ-1068](https://jira.mariadb.org/browse/CONJ-1068)] ResultSetMetaData.getColumnTypeName() returns VARCHAR instead of TINYTEXT
* [Revision #d094b858](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d094b858) - \[misc] adding java 21 to test suite
* [Revision #663d6917](https://github.com/mariadb-corporation/mariadb-connector-j/commit/663d6917) - \[misc] avoid fingerprint verification if certificate expired
* [Revision #877dc25c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/877dc25c) - \[misc] bump dependencies
* [Revision #39eab5bd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/39eab5bd) - bump 2.4.1-SNAPSHOT version
* [Revision #9667c76c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9667c76c) - \[[CONJ-1185](https://jira.mariadb.org/browse/CONJ-1185)] error CANON\_EQ flag not supported in Android app
* [Revision #7f2ff7eb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7f2ff7eb) - \[misc] mysql 8.4 test correction: adding serverRsaPublicKeyFile in test
* [Revision #907a99b1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/907a99b1) - \[misc] test addition: set allowPublicKeyRetrieval to true for mysql 8.4 by default
* [Revision #0db5648c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0db5648c) - \[misc] test correction for mysql\_clear\_password used in non SSL connections

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
