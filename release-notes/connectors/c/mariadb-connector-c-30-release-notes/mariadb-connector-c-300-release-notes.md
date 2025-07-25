# Connector/C 3.0.0 Release Notes

The most recent [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/C is:[**MariaDB Connector/C 3.4.5**](../mariadb-connector-c-3-4-release-notes/mariadb-connector-c-3-4-5-release-notes.md)

[Download](https://downloads.mariadb.org/connector-c/3.0.0)[Release Notes](mariadb-connector-c-300-release-notes.md)[About MariaDB Connector/C](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-c/README.md)

**Release date:** 20 Jan 2016

This is an [_Alpha_](../../../community-server/about/release-criteria.md) release of MariaDB Connector/C,\
formerly known as the MariaDB Client Library for C. As with any other\
pre-production release, cautions should be taken when installing on production\
systems or systems with critical data. Not all of the features, planned for the\
final MariaDB Connector/C 3.0 release are implemented yet.

**For a description of this library see the**[**MariaDB Connector/C**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-c) **page.**

## Download

Binary packages for Windows (32 and 64-bit) and generic Linux packages as well\
as source code packages are available from the [MariaDB download page](https://downloads.mariadb.org/connector-c/3.0.0)

## New features

### SSL

* In addition to OpenSSL the following SSL libraries are supported in Connector/C 3.0:
  * GnuTLS
  * Windows Schannel. SChannel requires no other external libraries besides the Windows system libraries, and is the default for SSL Support on Windows operating systems.
* Support of the TLSv1.1 and TLSv1.2 protocols.
* Support of passphrase protected private keys.

### Plugins

All plugins can either be linked statically or built as shared objects (or\
dynamic link libraries on Windows)

* pluggable Virtual IO (PVIO) for communication via socket, named pipe and shared memory
* connection plugins, e.g for aurora failover or replication (master write, slave read)
* remote IO plugin, which allows to access remote files (via http, https, ftp, ldap, ..)
* Trace plugin (for analyzing and dumping network traffic)

### New API functions

* mariadb\_get\_info and mariadb\_get\_infov (variable argument list) for obtaining general and connection specific values.
* mariadb\_get\_charset\_by\_name and mariadb\_get\_charset\_by\_nr which return charset information for a given internal number or name of character set.\
  These functions have been previously used internally by MariaDB Connector/ODBC and are now exported, so they can be used also within plugins.
* mysql\_get\_option and mysql\_get\_optionv (variable argument list) for obtaining option values for a given connection.
* mysql\_reconnect which was used internally before (if the option MYSQL\_OPT\_RECONNECT was set) is now part of the API and can be used by applications and plugins to reestablish a failing connection

We will cover new functionality in detail with a couple of blog entries during\
the next days. The first one "What's new in Connector/C 3.0: Part I SSL" can be\
found [here](https://mariadb.org/whats-new-in-mariadb-connectorc-3-0-part-i-ssl/)

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
