# MariaDB Connector/J 3.4.0 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](../../3.4/mariadb-connector-j-3-4-0-release-notes.md)[Changelog](mariadb-connector-j-3-4-0-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 17 May 2024

For the highlights of this release, see the [release notes](../../3.4/mariadb-connector-j-3-4-0-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #92d8414d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/92d8414d) - Merge branch 'develop'
* [Revision #474e9690](https://github.com/mariadb-corporation/mariadb-connector-j/commit/474e9690) - bump 3.4.0
* [Revision #c9786f2c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c9786f2c) - \[[CONJ-1173](https://jira.mariadb.org/browse/CONJ-1173)] Bulk implementation returning individual results
* [Revision #da506473](https://github.com/mariadb-corporation/mariadb-connector-j/commit/da506473) - \[misc] metadata ensure correct join in case of using catalog in the future
* [Revision #4a0b526d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4a0b526d) - \[[CONJ-1171](https://jira.mariadb.org/browse/CONJ-1171)] ensure compatibility with 3.x current behavior
* [Revision #0a7a094c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0a7a094c) - \[[CONJ-1174](https://jira.mariadb.org/browse/CONJ-1174)] wrong value for ResultSetMetaData.getPrecision() signed numeric
* [Revision #365d6a35](https://github.com/mariadb-corporation/mariadb-connector-j/commit/365d6a35) - \[misc] avoid fallthrough warning
* [Revision #e0aff1e1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e0aff1e1) - \[misc] avoid checking redirection for empty string value
* [Revision #4567d3ba](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4567d3ba) - \[[CONJ-1171](https://jira.mariadb.org/browse/CONJ-1171)] timezone new options \* connectionTimeZone \* forceConnectionTimeZoneToSession \* preserveInstants
* [Revision #74e581b0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/74e581b0) - \[[CONJ-1100](https://jira.mariadb.org/browse/CONJ-1100)] ensure DatabaseMetaData.getTables() returning mysql, performance\_schema and sys as system tables/views, to permit filtering only user tables/view
* [Revision #5e243b1e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5e243b1e) - \[[CONJ-1125](https://jira.mariadb.org/browse/CONJ-1125)] follow JDBC spec PreparedStatement/PreparedStatement.executeQuery must throw exception when no returning result-set. This is the exact difference of when not using .execute();
* [Revision #89ef4bfb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/89ef4bfb) - \[[CONJ-1170](https://jira.mariadb.org/browse/CONJ-1170)] correct DatabaseMetaData.getSQLKeywords(), parsing from MariaDB source code (sql/lex.h)
* [Revision #fc791bc5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fc791bc5) - \[[CONJ-1103](https://jira.mariadb.org/browse/CONJ-1103)] support for nullDatabaseMeansCurrent (alias for nullCatalogMeansCurrent)
* [Revision #99442c17](https://github.com/mariadb-corporation/mariadb-connector-j/commit/99442c17) - \[[CONJ-1107](https://jira.mariadb.org/browse/CONJ-1107)] support query timeout even if server doesn't support SET STATEMENT max\_statement\_time=xx
* [Revision #ec22ae30](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ec22ae30) - \[[CONJ-1168](https://jira.mariadb.org/browse/CONJ-1168)] test correction
* [Revision #746924de](https://github.com/mariadb-corporation/mariadb-connector-j/commit/746924de) - bump 3.4.0 snapshot
* [Revision #b8c8189d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b8c8189d) - \[[CONJ-1169](https://jira.mariadb.org/browse/CONJ-1169)] improve Client prepared statement setMaxRows implementation
* [Revision #42df505e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/42df505e) - \[[CONJ-1168](https://jira.mariadb.org/browse/CONJ-1168)] useBulkStmts compatibility value with pre 3.2 version
* [Revision #aecb270b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/aecb270b) - \[misc] ensure not using executeQuery when no result-set is returned
* [Revision #56c5b395](https://github.com/mariadb-corporation/mariadb-connector-j/commit/56c5b395) - \[misc] follow JDBC spec PreparedStatement.executeQuery must throw exception when no returning result-set
* [Revision #17fa51e8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/17fa51e8) - \[[CONJ-1166](https://jira.mariadb.org/browse/CONJ-1166)] new fallbackToSystemKeyStore and fallbackToSystemTrustStore option to permit preventing use of default java key/truststore
* [Revision #cc0e0a16](https://github.com/mariadb-corporation/mariadb-connector-j/commit/cc0e0a16) - \[[CONJ-1154](https://jira.mariadb.org/browse/CONJ-1154)] avoid unnecessary set transaction isolation queries
* [Revision #ee3844c1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ee3844c1) - \[[CONJ-1087](https://jira.mariadb.org/browse/CONJ-1087)] correcting test for MySQL 8 using transaction\_isolation in place of tx\_isolation
* [Revision #b32cd5c1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b32cd5c1) - \[misc] wrap ReentrantLock into AutoCloseable to ensure proper closing
* [Revision #93b275e9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/93b275e9) - \[[CONJ-1087](https://jira.mariadb.org/browse/CONJ-1087)] use transaction\_isolation in place of tx\_isolation and @@session.\[transaction\_read\_only|tx\_read\_only] in place of SET SESSION TRANSACTION READ ONLY, in order to avoid multiple commands on connection creation
* [Revision #168ab3c1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/168ab3c1) - \[[CONJ-1158](https://jira.mariadb.org/browse/CONJ-1158)] test stability for all server version
* [Revision #c6e9f0a1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c6e9f0a1) - \[[CONJ-1163](https://jira.mariadb.org/browse/CONJ-1163)] new option 'jdbcCompliantTruncation' default true
* [Revision #6da60da3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6da60da3) - \[[CONJ-1158](https://jira.mariadb.org/browse/CONJ-1158)] test stability for all server version
* [Revision #a95787e7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a95787e7) - \[misc] ensure stable test for socket timeout on windows + code style correction
* [Revision #90793e06](https://github.com/mariadb-corporation/mariadb-connector-j/commit/90793e06) - \[[CONJ-1156](https://jira.mariadb.org/browse/CONJ-1156)] DatabaseMetaData#getTables's result not property ordered
* [Revision #d8b31300](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d8b31300) - \[[CONJ-1158](https://jira.mariadb.org/browse/CONJ-1158)] DatabaseMetaData#getFunctions's result not property ordered
* [Revision #6030e6d0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6030e6d0) - \[[CONJ-1159](https://jira.mariadb.org/browse/CONJ-1159)] DatabaseMetaData#getClientInfoProperties not ordered correctly
* [Revision #eea8b3b7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/eea8b3b7) - Merge branch 'develop' into feature/[CONJ-731](https://jira.mariadb.org/browse/CONJ-731)
* [Revision #70acc9ad](https://github.com/mariadb-corporation/mariadb-connector-j/commit/70acc9ad) - \[[CONJ-1105](https://jira.mariadb.org/browse/CONJ-1105)] avoid hostname validation for validated self-signed certificates
* [Revision #38639ca2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/38639ca2) - \[[CONJ-731](https://jira.mariadb.org/browse/CONJ-731)] Connection Redirection Mechanism implementation
* [Revision #4ef7fb8f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4ef7fb8f) - \[[CONJ-1105](https://jira.mariadb.org/browse/CONJ-1105)] test correction for enterprise server
* [Revision #46ee91d8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/46ee91d8) - \[[CONJ-1105](https://jira.mariadb.org/browse/CONJ-1105)] avoid ssl client configuration when possible
* [Revision #faf44089](https://github.com/mariadb-corporation/mariadb-connector-j/commit/faf44089) - \[misc] code style format correction
* [Revision #233a0d4c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/233a0d4c) - \[misc] add contributor list
* [Revision #622db978](https://github.com/mariadb-corporation/mariadb-connector-j/commit/622db978) - \[misc] add java 21 to CI
* [Revision #b3700257](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b3700257) - \[[CONJ-1163](https://jira.mariadb.org/browse/CONJ-1163)] jdbcCompliantTruncation option addition
* [Revision #9f997881](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9f997881) - \[misc] code style correction
* [Revision #8585e687](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8585e687) - \[misc] test correction when server use `pam_use_cleartext_plugin` configuration
* [Revision #02406490](https://github.com/mariadb-corporation/mariadb-connector-j/commit/02406490) - \[[CONJ-1164](https://jira.mariadb.org/browse/CONJ-1164)] permit multi queries with LOAD DATA INFILE
* [Revision #6585f4c3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6585f4c3) - \[[CONJ-1161](https://jira.mariadb.org/browse/CONJ-1161)] compatible Android RegExp

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
