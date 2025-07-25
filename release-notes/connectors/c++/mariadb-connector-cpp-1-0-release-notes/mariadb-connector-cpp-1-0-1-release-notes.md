# Connector/C++ 1.0.1 Release Notes

The most recent [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/C++ is:[**MariaDB Connector/C++ 1.1.6**](../mariadb-connector-cpp-1-1-release-notes/mariadb-connector-cpp-1-1-6-release-notes.md)

[Download Now](https://mariadb.com/downloads/connectors/connectors-data-access/cpp-connector)

**Release date:** 2021-06-17

This is a [_**Stable (GA)**_](../../../community-server/about/release-criteria.md) release of MariaDB Connector/C++.

**For a description of this library see the**[**MariaDB Connector/C++**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-cpp) **page.**

[MariaDB Connector/C++](broken-reference) is the interface between C++ applications and MariaDB Server. MariaDB Connector/C++ enables development of C++ applications using a JDBC-based API, which is also used by MariaDB Connector/J.

MariaDB Connector/C++ implements the MySQL protocol using the MariaDB Connector/C API. This release depends on MariaDB Connector/C 3.1.13.

## Notable Changes

* Adds `useCharacterEncoding` connection string option to control the character set used for connection, input, and results. Includes `OPT_SET_CHARSET_NAME` and `useCharset` aliases for compatibility. ([CONCPP-78](https://jira.mariadb.org/browse/CONCPP-78))
* Adds `credentialType` connection string option to set the default client-side authentication plugin, similar to `MYSQL_DEFAULT_AUTH` in MariaDB Connector/C. Includes `defaultAuth` alias for compatibility. ([CONCPP-84](https://jira.mariadb.org/browse/CONCPP-84))

## Issues Fixed

* Metadata retrieved from [mysql.proc](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/the-mysql-database-tables/mysql-proc-table) instead of using the Information Schema. ([CONCPP-69](https://jira.mariadb.org/browse/CONCPP-69))
* CMake generates an error on nesting of flow control statements. ([CONCPP-79](https://jira.mariadb.org/browse/CONCPP-79))
* CMake fails when called without the `-DWITH_SSL=OpenSSL` option. ([CONCPP-80](https://jira.mariadb.org/browse/CONCPP-80))
* Sub-directory install paths include a dot (`./`) directory, which is not correct. ([CONCPP-81](https://jira.mariadb.org/browse/CONCPP-81))

## Installation

[Install MariaDB Connector/C++](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-cpp/install-mariadb-connector-cpp)

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
