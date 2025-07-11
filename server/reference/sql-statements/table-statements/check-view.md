# CHECK VIEW

## Syntax

```
CHECK VIEW view_name
```

## Description

The `CHECK VIEW` statement was introduced in [MariaDB 10.0.18](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-10-0-series/mariadb-10018-release-notes) to assist with fixing [MDEV-6916](https://jira.mariadb.org/browse/MDEV-6916), an issue introduced in [MariaDB 5.2](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-5-2-series/changes-improvements-in-mariadb-5-2) where the view algorithms were swapped. It checks whether the view algorithm is correct. It is run as part of [mariadb-upgrade](../../../clients-and-utilities/deployment-tools/mariadb-upgrade.md), and should not normally be required in regular use.

## See Also

* [REPAIR VIEW](repair-view.md)

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
