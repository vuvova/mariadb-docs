# MariaDB Connector/J 3.5.0 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](../../3.5/mariadb-connector-j-3-5-0-release-notes.md)[Changelog](mariadb-connector-j-3-5-0-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 24 Oct 2024

For the highlights of this release, see the [release notes](../../3.5/mariadb-connector-j-3-5-0-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #8be57f3b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8be57f3b) \[[CONJ-1205](https://jira.mariadb.org/browse/CONJ-1205)] permit setObject with ARRAY dataType
* [Revision #3e948485](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3e948485) \[[CONJ-1205](https://jira.mariadb.org/browse/CONJ-1205)] permit use of Array parameter
* [Revision #a54a87ed](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a54a87ed) \[misc] update readme version
* [Revision #ae8e740d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ae8e740d) \[misc] permit using setObject/getObject on float\[]/Float\[] values
* [Revision #54635728](https://github.com/mariadb-corporation/mariadb-connector-j/commit/54635728) \[misc] code style correction
* [Revision #91c06e6e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/91c06e6e) Merge branch 'develop'
* [Revision #1ce59828](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1ce59828) \[misc] XA Pool datasource ensuring close when using XAConnection.close()
* [Revision #a81f0e38](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a81f0e38) \[misc] XA test correction
* [Revision #a66f05d2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a66f05d2) \[misc] test correction for ES server
* [Revision #32ca5d75](https://github.com/mariadb-corporation/mariadb-connector-j/commit/32ca5d75) \[misc] changing testing option disableSessionTracking defaut value
* [Revision #7d66c42d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7d66c42d) Merge branch 'develop'
* [Revision #24fa8659](https://github.com/mariadb-corporation/mariadb-connector-j/commit/24fa8659) bump 3.5.0
* [Revision #b7fb53fe](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b7fb53fe) \[misc] code coverage addition
* [Revision #50b78dce](https://github.com/mariadb-corporation/mariadb-connector-j/commit/50b78dce) \[[CONJ-1201](https://jira.mariadb.org/browse/CONJ-1201)] incorrect default behavior for forceConnectionTimeZoneToSession - test addition
* [Revision #9cd567ca](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9cd567ca) \[[CONJ-1201](https://jira.mariadb.org/browse/CONJ-1201)] incorrect default behavior for forceConnectionTimeZoneToSession
* [Revision #418a157f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/418a157f) \[misc] MySQL test speed improvement
* [Revision #457561a7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/457561a7) \[misc] improve failover test stability - second part
* [Revision #4b6cc77e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4b6cc77e) \[misc] improve failover test stability
* [Revision #63d1436d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/63d1436d) \[[CONJ-1183](https://jira.mariadb.org/browse/CONJ-1183)] missing providing other TLS truststore than default java one
* [Revision #9087d054](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9087d054) \[misc] badge link correction
* [Revision #f7fc6aaa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f7fc6aaa) \[misc] code coverage improvement
* [Revision #3df99168](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3df99168) \[[CONJ-1187](https://jira.mariadb.org/browse/CONJ-1187)] throw an explicit type SQLTimeoutException in place of SQLNonTransientConnectionException when connection fail because of timeout
* [Revision #8741f858](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8741f858) \[misc] test stability improvement
* [Revision #c048ce73](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c048ce73) \[test] collation test correction
* [Revision #b369aceb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b369aceb) \[[CONJ-1202](https://jira.mariadb.org/browse/CONJ-1202)] Session variable setting must be executed last
* [Revision #9b69c211](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9b69c211) \[[CONJ-1199](https://jira.mariadb.org/browse/CONJ-1199)] adding option connectionCollation in order to set utf8mb4 collation that differ from default utf8mb4 collation
* [Revision #ded788f7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ded788f7) \[[CONJ-1200](https://jira.mariadb.org/browse/CONJ-1200)] BULK big parameters might be sent without bulk header, resulting in "Unknown command"
* [Revision #6316ba81](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6316ba81) bump 3.4.2 snapshot
* [Revision #a788d40e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a788d40e) \[misc] test stability correction
* [Revision #b5ae7e78](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b5ae7e78) \[misc] test stability correction
* [Revision #90111fbf](https://github.com/mariadb-corporation/mariadb-connector-j/commit/90111fbf) \[misc] test correction, ensuring certificate content won't break test
* [Revision #46628b22](https://github.com/mariadb-corporation/mariadb-connector-j/commit/46628b22) \[misc] logging test addition
* [Revision #3657cd62](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3657cd62) \[misc] avoiding String creation when not needed
* [Revision #5cdf06d7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5cdf06d7) \[misc] documentation correction

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
