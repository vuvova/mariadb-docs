# MariaDB Connector/J 2.3.0 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.3.0/)[Release Notes](../../2.3/mariadb-connector-j-230-release-notes.md)[Changelog](mariadb-connector-j-230-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 7 Sep 2018

For the highlights of this release, see the [release notes](../../2.3/mariadb-connector-j-230-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #84ad1cff](https://github.com/mariadb-corporation/mariadb-connector-j/commit/84ad1cff) - tag 2.3.0
* [Revision #49c3e41e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/49c3e41e) - \[misc] remove MariaDbDataSource.setURL() method, deprecated since 1.3
* [Revision #8afce383](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8afce383) - \[[CONJ-641](https://jira.mariadb.org/browse/CONJ-641)] update maven dependencies for java 10 compatibilities
* [Revision #359afa1e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/359afa1e) - \[[CONJ-643](https://jira.mariadb.org/browse/CONJ-643)] update maven dependencies for java 10 compatibilities
* [Revision #7b0c9321](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7b0c9321) - \[[CONJ-643](https://jira.mariadb.org/browse/CONJ-643)] PreparedStatement::getParameterMetaData always returns VARSTRING as type resulting in downstream libraries interpreting values wrongly
* [Revision #a75555f6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a75555f6) - \[[CONJ-398](https://jira.mariadb.org/browse/CONJ-398)] Improve deadlock debugging capabilties
* [Revision #a3ee75b0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a3ee75b0) - \[[CONJ-642](https://jira.mariadb.org/browse/CONJ-642)] travis correction to permit testing option "rewriteBatchedStatements" - part 2
* [Revision #ed79b544](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ed79b544) - \[[CONJ-642](https://jira.mariadb.org/browse/CONJ-642)] travis correction to permit testing option "rewriteBatchedStatements"
* [Revision #141dd932](https://github.com/mariadb-corporation/mariadb-connector-j/commit/141dd932) - \[[CONJ-642](https://jira.mariadb.org/browse/CONJ-642)] travis activating testing option "useBulkStmts"
* [Revision #e7c0940c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e7c0940c) - \[[CONJ-642](https://jira.mariadb.org/browse/CONJ-642)] correcting test when not rewritable and option "useBulkStmts" not set
* [Revision #89c9e5da](https://github.com/mariadb-corporation/mariadb-connector-j/commit/89c9e5da) - \[[CONJ-639](https://jira.mariadb.org/browse/CONJ-639)] enabledSslProtocolSuites now permit TLSv1.2 by default
* [Revision #fc92233e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fc92233e) - \[[CONJ-642](https://jira.mariadb.org/browse/CONJ-642)] disable the option "useBulkStmts" by default
* [Revision #0013ee92](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0013ee92) - \[[CONJ-616](https://jira.mariadb.org/browse/CONJ-616)] correcting possible NPE in case of master down and option "allowMasterDownConnection" is set
* [Revision #4c318fdd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4c318fdd) - \[misc] correcting tests for PR not having access to aurora test
* [Revision #839902d4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/839902d4) - \[[CONJ-634](https://jira.mariadb.org/browse/CONJ-634)] adding javadoc documentation
* [Revision #fb81de35](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fb81de35) - \[[CONJ-634](https://jira.mariadb.org/browse/CONJ-634)] avoid import of non dependency to permit compilation Ahead of time
* [Revision #fe6954ff](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fe6954ff) - \[[CONJ-637](https://jira.mariadb.org/browse/CONJ-637)] Driver.getPropertyInfo() implementation
* [Revision #a4fe8a65](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a4fe8a65) - \[[CONJ-616](https://jira.mariadb.org/browse/CONJ-616)] avoiding NPE on connection when using master slave configuration and no host found
* [Revision #fabfb3c8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fabfb3c8) - \[misc] correcting appveyor maven installation to 3.5.4
* [Revision #c16cfc33](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c16cfc33) - \[misc] correcting appveyor maven installation to 3.5.4
* [Revision #0fe442e3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0fe442e3) - \[[CONJ-636](https://jira.mariadb.org/browse/CONJ-636)] correcting possible NPE thrown in place of exception
* [Revision #4b0f7bbb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4b0f7bbb) - \[misc] updating appveyor maven to new version 3.5.4
* [Revision #25e1f5d3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/25e1f5d3) - \[misc] updating appveyor maven to new version 3.5.4
* [Revision #d92ae73c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d92ae73c) - \[[CONJ-628](https://jira.mariadb.org/browse/CONJ-628)] small optimization to read metadata faster
* [Revision #d4fcfbeb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d4fcfbeb) - [CONJ-623](https://jira.mariadb.org/browse/CONJ-623) / Increase connection logging when Primary node connection fails
* [Revision #b24e66b0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b24e66b0) - fixed formatting
* [Revision #eac3d315](https://github.com/mariadb-corporation/mariadb-connector-j/commit/eac3d315) - Update MariaDbPoolDataSource.java

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
