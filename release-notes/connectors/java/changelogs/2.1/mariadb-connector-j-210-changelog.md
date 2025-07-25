# MariaDB Connector/J 2.1.0 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.1.0/)[Release Notes](../../2.1/mariadb-connector-j-210-release-notes.md)[Changelog](mariadb-connector-j-210-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 31 July 2017

For the highlights of this release, see the [release notes](../../2.1/mariadb-connector-j-210-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #501b9129](https://github.com/mariadb-corporation/mariadb-connector-j/commit/501b9129) - \[misc] checkstyle correction
* [Revision #45be8ac9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/45be8ac9) - \[misc] using dns mariadb.example.com for SSL tests for hostname verification
* [Revision #a3c6b446](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a3c6b446) - \[misc] travis hostname change for hostname verification
* [Revision #c6b10331](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c6b10331) - correcting changelog
* [Revision #e0bdf02c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e0bdf02c) - Merge tag '2.1.0' into develop
* [Revision #62d3f8b4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/62d3f8b4) - Merge branch 'release/2.1.0'
* [Revision #74e851f8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/74e851f8) - bump 2.1.0 version
* [Revision #3ae2659b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3ae2659b) - \[[CONJ-422](https://jira.mariadb.org/browse/CONJ-422)] Provide verification of SSL Certificate Name Mismatch
* [Revision #5f7eab9b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5f7eab9b) - \[[CONJ-502](https://jira.mariadb.org/browse/CONJ-502)] isolation correction on failover when using multiple pools on same VM - part 3
* [Revision #18e9b32c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/18e9b32c) - \[misc] test correction to ensure error message after packet > to max\_allowed\_packet
* [Revision #3cafb677](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3cafb677) - Merge remote-tracking branch 'origin/develop' into develop
* [Revision #f20e5163](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f20e5163) - \[[CONJ-389](https://jira.mariadb.org/browse/CONJ-389)] implement new COM\_STMT\_BULK\_EXECUTE command for MariaDB server >= 10.2.7 for fast batch execution
* [Revision #1a324baf](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1a324baf) - \[[CONJ-492](https://jira.mariadb.org/browse/CONJ-492)] failover KILL test ignore for maxscale
* [Revision #66da9694](https://github.com/mariadb-corporation/mariadb-connector-j/commit/66da9694) - \[[CONJ-492](https://jira.mariadb.org/browse/CONJ-492)] test correction (MySQL server doesn't make the distinction if query was kill and connection is killed).
* [Revision #7647d7c5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7647d7c5) - \[misc] code checkstyle correction
* [Revision #4202e8de](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4202e8de) - \[[CONJ-492](https://jira.mariadb.org/browse/CONJ-492)] Failover handle reconnect on KILL command
* [Revision #7cb369f6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7cb369f6) - \[misc] add deprecation on CallableStatement.getBigDecimal(int parameterIndex, int scale) (as in Java API)
* [Revision #b3b65364](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b3b65364) - \[[CONJ-503](https://jira.mariadb.org/browse/CONJ-503)] regression on aurora Connection.isReadOnly()
* [Revision #27f6cbf8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/27f6cbf8) - \[[CONJ-502](https://jira.mariadb.org/browse/CONJ-502)] isolation correction on failover when using multiple pools on same VM - part 2
* [Revision #80206183](https://github.com/mariadb-corporation/mariadb-connector-j/commit/80206183) - \[misc] aurora unique cluster validation
* [Revision #ed2e05ab](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ed2e05ab) - \[misc] aurora cluster detection ignore case
* [Revision #430583bb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/430583bb) - \[[CONJ-502](https://jira.mariadb.org/browse/CONJ-502)] isolation correction on failover when using multiple pools on same VM
* [Revision #b0ecfc24](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b0ecfc24) - \[[CONJ-322](https://jira.mariadb.org/browse/CONJ-322)] ResultSet.update\* implementation - using virtual insert row in respect of java API philosophy
* [Revision #ed270f9c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ed270f9c) - \[[CONJ-322](https://jira.mariadb.org/browse/CONJ-322)] ResultSet.update\* implementation
* [Revision #9ab2be84](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9ab2be84) - Merge remote-tracking branch 'origin/develop' into develop
* [Revision #c7765f34](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c7765f34) - \[[CONJ-508](https://jira.mariadb.org/browse/CONJ-508)] Connection.getCatalog() optimisation for 10.2+ server
* [Revision #44a176f3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/44a176f3) - \[[CONJ-506](https://jira.mariadb.org/browse/CONJ-506)] metadata.getColumn default value test correction since [MDEV-1332](https://jira.mariadb.org/browse/MDEV-1332)
* [Revision #1453babc](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1453babc) - Merge remote-tracking branch 'origin/master'
* [Revision #16637e0d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/16637e0d) - \[[CONJ-506](https://jira.mariadb.org/browse/CONJ-506)] metadata.getColumn default value test correction since [MDEV-1332](https://jira.mariadb.org/browse/MDEV-1332)
* [Revision #424e0897](https://github.com/mariadb-corporation/mariadb-connector-j/commit/424e0897) - \[CONJ 506] column metadata return 'null' in place of null for server 10.2.7
* [Revision #0488a1f7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0488a1f7) - \[CONJ 505] correcting issue that ended throwing Unknown prepared statement handler given
* [Revision #838b3662](https://github.com/mariadb-corporation/mariadb-connector-j/commit/838b3662) - \[misc] faster travis test if not using maxscale
* [Revision #f802d0f6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f802d0f6) - \[misc] adding test when using maxscale 2.0.6 and 2.1.4
* [Revision #c934c3c8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c934c3c8) - \[misc] maxscale correct docker installation
* [Revision #091da304](https://github.com/mariadb-corporation/mariadb-connector-j/commit/091da304) - \[misc] disabled some tests using maxscale until maxscale correct them
* [Revision #8a8e6cdc](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8a8e6cdc) - \[[CONJ-400](https://jira.mariadb.org/browse/CONJ-400)] galera primary mode validation in failover
* [Revision #9f31e503](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9f31e503) - \[[CONJ-400](https://jira.mariadb.org/browse/CONJ-400)] test correction for docker testing - variable correction
* [Revision #eff42c01](https://github.com/mariadb-corporation/mariadb-connector-j/commit/eff42c01) - \[[CONJ-400](https://jira.mariadb.org/browse/CONJ-400)] test correction for docker testing - part 2
* [Revision #b8cda994](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b8cda994) - \[[CONJ-400](https://jira.mariadb.org/browse/CONJ-400)] test correction for docker testing
* [Revision #d99e6722](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d99e6722) - \[[CONJ-400](https://jira.mariadb.org/browse/CONJ-400)] galera valid() specific implementation that doesn't just send a COM\_PING, but check that server is in primary mode
* [Revision #1cd578f5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1cd578f5) - \[[CONJ-327](https://jira.mariadb.org/browse/CONJ-327)] testing MySQL 5.7/8.0 compatibility with sha256Password - avoiding conflict with openssl installation
* [Revision #c0edaaea](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c0edaaea) - \[misc] travis docker testing : second relative path correction for forking
* [Revision #c50d3722](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c50d3722) - \[misc] travis docker testing : relative path correction
* [Revision #cb95cac3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/cb95cac3) - \[misc] travis docker testing : changing to relative path, permitting forks
* [Revision #b6d4c859](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b6d4c859) - \[misc] travis docker test : correcting bash header
* [Revision #f0bcbaf6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f0bcbaf6) - \[misc] travis docker test : change sleep time to permit to database to reboot before maxscale connection
* [Revision #8040bbc3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8040bbc3) - \[[CONJ-422](https://jira.mariadb.org/browse/CONJ-422)] add documentation and better error description
* [Revision #6ef2ed0c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6ef2ed0c) - Merge pull request #109 from krisiye/[CONJ-496](https://jira.mariadb.org/browse/CONJ-496)
* [Revision #e7df7d15](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e7df7d15) - Updates to the comments to reflect decimal parsing.
* [Revision #ed81a136](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ed81a136) - \[misc] better compatible version visibility
* [Revision #4b7f2653](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4b7f2653) - \[misc] changing logo
* [Revision #9c18956b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9c18956b) - Create CONTRIBUTING.md
* [Revision #3d0b8c38](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3d0b8c38) - \[[CONJ-422](https://jira.mariadb.org/browse/CONJ-422)] add documentation and better error description

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
