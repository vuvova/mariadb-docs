# MariaDB MaxScale 23.08.5 Release Notes

## MaxScale 23.08 MariaDB MaxScale 23.08.5 Release Notes -- 2024-03-11

## MariaDB MaxScale 23.08.5 Release Notes -- 2024-03-11

Release 23.08.5 is a GA release.

This document describes the changes in release 23.08.5, when compared to the\
previous release in the same series.

If you are upgrading from an older major version of MaxScale, please read the [upgrading document](https://mariadb.com/docs/maxscale/maxscale-versions/mariadb-maxscale-24-02/maxscale-24-02upgrading/mariadb-maxscale-2402-maxscale-2402-upgrading-mariadb-maxscale-from-2302-to-2308) for\
this MaxScale version.

For any problems you encounter, please consider submitting a bug\
report on [our Jira](https://jira.mariadb.org/projects/MXS).

### External CVEs resolved.

* [CVE-2023-1667](https://www.cve.org/CVERecord?id=CVE-2023-1667) Fixed by [MXS-5011](https://jira.mariadb.org/browse/MXS-5011) Upgrade libssh to 0.10.6
* [CVE-2023-2283](https://www.cve.org/CVERecord?id=CVE-2023-2283) Fixed by [MXS-5011](https://jira.mariadb.org/browse/MXS-5011) Upgrade libssh to 0.10.6
* [CVE-2023-6004](https://www.cve.org/CVERecord?id=CVE-2023-6004) Fixed by [MXS-5011](https://jira.mariadb.org/browse/MXS-5011) Upgrade libssh to 0.10.6
* [CVE-2023-6918](https://www.cve.org/CVERecord?id=CVE-2023-6918) Fixed by [MXS-5011](https://jira.mariadb.org/browse/MXS-5011) Upgrade libssh to 0.10.6
* [CVE-2023-48795](https://www.cve.org/CVERecord?id=CVE-2023-48795) Fixed by [MXS-5011](https://jira.mariadb.org/browse/MXS-5011) Upgrade libssh to 0.10.6

### New Features

* [MXS-4917](https://jira.mariadb.org/browse/MXS-4917) Add disk\_space\_ok option to master\_conditions and slave\_conditions

### Bug fixes

* [MXS-5008](https://jira.mariadb.org/browse/MXS-5008) Log message on releasing exclusive locks when no lock majority is confusing
* [MXS-5007](https://jira.mariadb.org/browse/MXS-5007) Top-level service reconnection may cause a use-after-free
* [MXS-5001](https://jira.mariadb.org/browse/MXS-5001) Maxscale fail to initiate maxscale.service (Missing /var/run/maxscale) directory
* [MXS-4998](https://jira.mariadb.org/browse/MXS-4998) MaxScale may send two COM\_QUIT packets
* [MXS-4997](https://jira.mariadb.org/browse/MXS-4997) MaxScale: BUILD/install\_build\_deps.sh: deprecated --force-yes
* [MXS-4996](https://jira.mariadb.org/browse/MXS-4996) Order of servers is different after restart if runtime modifications have been done
* [MXS-4995](https://jira.mariadb.org/browse/MXS-4995) The "static" property of an object is lost upon restart
* [MXS-4994](https://jira.mariadb.org/browse/MXS-4994) Multiple warnings from the REST-API are printed on the same line
* [MXS-4992](https://jira.mariadb.org/browse/MXS-4992) Documentation Link in GUI leads to 404 page not found
* [MXS-4988](https://jira.mariadb.org/browse/MXS-4988) maxscale doesn't properly close connections for TCP health check probes
* [MXS-4982](https://jira.mariadb.org/browse/MXS-4982) OpenSSL system call error is logged as ERROR when client disconnects abruptly
* [MXS-4981](https://jira.mariadb.org/browse/MXS-4981) Hang on shutdown when large batches of session command are pending
* [MXS-4979](https://jira.mariadb.org/browse/MXS-4979) COM\_CHANGE\_USER may leave stale IDs to be checked
* [MXS-4978](https://jira.mariadb.org/browse/MXS-4978) Read-only transactions are incorrectly tracked
* [MXS-4969](https://jira.mariadb.org/browse/MXS-4969) Can't create more than max\_prepared\_stmt\_count statements
* [MXS-4968](https://jira.mariadb.org/browse/MXS-4968) REST-API TLS certificates can be reloaded but the path to them cannot be altered
* [MXS-4967](https://jira.mariadb.org/browse/MXS-4967) Log throttling is sometimes disabled too early
* [MXS-4961](https://jira.mariadb.org/browse/MXS-4961) Result of KILL CONNECTION\_ID() does not propagate all the way to the client
* [MXS-4956](https://jira.mariadb.org/browse/MXS-4956) Session commands ignore delayed\_retry\_timeout
* [MXS-4948](https://jira.mariadb.org/browse/MXS-4948) Unable to see columns of view in the Query Editor
* [MXS-4947](https://jira.mariadb.org/browse/MXS-4947) Tables in information\_schema are treated as a normal tables
* [MXS-4945](https://jira.mariadb.org/browse/MXS-4945) GUI doesn't validate object name uniqueness accurately
* [MXS-4943](https://jira.mariadb.org/browse/MXS-4943) delayed\_retry timeout errors do not have enough information
* [MXS-4935](https://jira.mariadb.org/browse/MXS-4935) False protocol incompatibility error
* [MXS-4934](https://jira.mariadb.org/browse/MXS-4934) Use-after-free after service deletion
* [MXS-4930](https://jira.mariadb.org/browse/MXS-4930) 'maxctrl reload tls' has the usage of 'maxctrl reload service'
* [MXS-4926](https://jira.mariadb.org/browse/MXS-4926) History length of sessions is not visible in the REST-API
* [MXS-4925](https://jira.mariadb.org/browse/MXS-4925) self link in /maxscale/logs/data is off by one page
* [MXS-4924](https://jira.mariadb.org/browse/MXS-4924) Very fast client and server may end up busy-looping a worker
* [MXS-4922](https://jira.mariadb.org/browse/MXS-4922) Memory growth for long-running sessions that use COM\_CHANGE\_USER
* [MXS-4921](https://jira.mariadb.org/browse/MXS-4921) Memory growth for long-running sessions that use prepared statements
* [MXS-4914](https://jira.mariadb.org/browse/MXS-4914) GUI dashboard's width is reduced unexpectedly
* [MXS-4912](https://jira.mariadb.org/browse/MXS-4912) Query classifier cache total-size book-keeping may be wrong
* [MXS-4910](https://jira.mariadb.org/browse/MXS-4910) readconnroute performance regression in 6.4
* [MXS-4907](https://jira.mariadb.org/browse/MXS-4907) Nested parameters in PATCH /v1/maxscale/ do not work correctly
* [MXS-4906](https://jira.mariadb.org/browse/MXS-4906) MonitorWorker::call\_run\_one\_tick() called more often than intended
* [MXS-4903](https://jira.mariadb.org/browse/MXS-4903) Bad configuration in PATCH may partially configure monitors
* [MXS-4901](https://jira.mariadb.org/browse/MXS-4901) Turning on log\_info causes parsing related errors and warnings
* [MXS-4900](https://jira.mariadb.org/browse/MXS-4900) maxctrl show qc\_cache can easily overwhelm MaxScale
* [MXS-4898](https://jira.mariadb.org/browse/MXS-4898) MaxScale sends wrong character set (session tracking)
* [MXS-4896](https://jira.mariadb.org/browse/MXS-4896) Reducing the size of the query classifier cache does not cause excess entries to be freed.
* [MXS-4893](https://jira.mariadb.org/browse/MXS-4893) Query history retention period increases unexpectedly every time the setting dialog is opened
* [MXS-4891](https://jira.mariadb.org/browse/MXS-4891) Query editor schema explorer is disabled after reconnecting connections
* [MXS-4888](https://jira.mariadb.org/browse/MXS-4888) Unable to type custom row limit in the Query configuration dialog
* [MXS-4879](https://jira.mariadb.org/browse/MXS-4879) Transaction state viewed from the session is different from the transaction state as viewed from RWS.
* [MXS-4865](https://jira.mariadb.org/browse/MXS-4865) 5.5.5- prefix should not be added if all backends are MariaDB 11

### Known Issues and Limitations

There are some limitations and known issues within this version of MaxScale.\
For more information, please refer to the [Limitations](../mariadb-maxscale-23-08-about/mariadb-maxscale-2308-limitations-and-known-issues-within-mariadb-maxscale.md) document.

### Packaging

RPM and Debian packages are provided for the supported Linux distributions.

Packages can be downloaded [here](https://mariadb.com/downloads/#mariadb_platform-mariadb_maxscale).

### Source Code

The source code of MaxScale is tagged at GitHub with a tag, which is identical\
with the version of MaxScale. For instance, the tag of version X.Y.Z of MaxScale\
is `maxscale-X.Y.Z`. Further, the default branch is always the latest GA version\
of MaxScale.

The source code is available [here](https://github.com/mariadb-corporation/MaxScale).

CC BY-SA / Gnu FDL
