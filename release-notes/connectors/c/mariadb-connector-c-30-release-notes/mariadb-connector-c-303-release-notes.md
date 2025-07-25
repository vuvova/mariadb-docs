# Connector/C 3.0.3 Release Notes

The most recent [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/C is:[**MariaDB Connector/C 3.4.5**](../mariadb-connector-c-3-4-release-notes/mariadb-connector-c-3-4-5-release-notes.md)

[Download](https://downloads.mariadb.org/connector-c/3.0.3)[Release Notes](mariadb-connector-c-303-release-notes.md)[Changelog](../changelogs/mariadb-connector-c-30-changelogs/mariadb-connector-c-303-changelog.md)[About MariaDB Connector/C](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-c/README.md)

**Release date:** 18 Jan 2018

This is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of the MariaDB\
Connector/C, formerly known as MariaDB Client Library for C.

**For a description of this library see the**[**MariaDB Connector/C**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-c) **page.**

## Features

* Added support for new utf8mb4 character sets
* New installation layout for Debian
* [MDEV-9059](https://jira.mariadb.org/browse/MDEV-9059): Bundle first command with authentication packet
* Build: support static OpenSSL on Windows
* [MDEV-14101](https://jira.mariadb.org/browse/MDEV-14101): Add support for tls-version, via mysql\_options(mysql, MARIADB\_OPT\_TLS\_VERSION, value), where value must be "TLSv1.1", "TLSv1.2" or "TLSv1.3".
* [CONC-275](https://jira.mariadb.org/browse/CONC-275): New indicator type STMT\_INDICATOR\_IGNORE\_ROW for skipping particular parameter set in bulk operation (prepared statements).

## Notable Bug fixes

* [MDEV-10361](https://jira.mariadb.org/browse/MDEV-10361): Don't try to reconnect twice if mysql\_ping failed.
* Build fix for TSAN build with Clang
* [CONC-302](https://jira.mariadb.org/browse/CONC-302): Fix output of mariadb\_config
* [CONC-301](https://jira.mariadb.org/browse/CONC-301): In case of a truncation the statement status was not updated correctly and further calls to mysql\_stmt\_fetch\_column failed
* [MDEV-14647](https://jira.mariadb.org/browse/MDEV-14647): Fixed crash when client receives extended ok packet with SESSION\_TRACK\_STATE\_CHANGE information flag
* [CONC-297](https://jira.mariadb.org/browse/CONC-297): setting MYSQL\_OPT\_LOCAL\_INFILE failed on big endian systems.
* [MDEV-14514](https://jira.mariadb.org/browse/MDEV-14514): mariadb\_config returned wrong exit code when specifying an invalid option
* [MDEV-11546](https://jira.mariadb.org/browse/MDEV-11546): Fixed timeout problem in Schannel
* [CONC-277](https://jira.mariadb.org/browse/CONC-277): Allow reinitialization of the library if mysql\_server\_end() was called.
* [MDEV-11603](https://jira.mariadb.org/browse/MDEV-11603): Solaris build fixes
* [CONC-292](https://jira.mariadb.org/browse/CONC-292): Fixed malloc result check in dynamic columns
* [MDEV-14165](https://jira.mariadb.org/browse/MDEV-14165): The metadata length value for a column with a zerofill flag was calculated with a fixed length instead of using the reported length.
* [CONC-286](https://jira.mariadb.org/browse/CONC-286): Force TLS/SSL usage if fingerprint parameters were specified.
* [CONC-282](https://jira.mariadb.org/browse/CONC-282): Connector/C now provides additional information for package version
  * mariadb\_config --cc\_version lists the package version
  * Beside MARIADB\_PACKAGE\_VERSION numeric representation MARIADB\_PACKAGE\_VERSION\_ID can be used now within preprocessor directives.
* [MDEV-13959](https://jira.mariadb.org/browse/MDEV-13959): Fixed duplicate if condition in dynamic columns
* Added MARIADB\_BASE\_VERSION definition in mariadb\_version.h to distnguish MARIADB from MySQL
* [CONC-276](https://jira.mariadb.org/browse/CONC-276): client library crashes on Windows after TLS reconnect
* [CONC-271](https://jira.mariadb.org/browse/CONC-271): installation layout fix for RPM

For a list of changes made in this release, with links to detailed\
information on each push, see the [changelog](../changelogs/mariadb-connector-c-30-changelogs/mariadb-connector-c-303-changelog.md).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
