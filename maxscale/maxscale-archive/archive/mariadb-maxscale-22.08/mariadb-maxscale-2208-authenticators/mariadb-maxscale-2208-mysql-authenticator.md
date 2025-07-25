# MaxScale 22.08 MySQL Authenticator

## MySQL Authenticator

## MariaDB/MySQL Authenticator

The _MariaDBAuth_-module implements the client and backend authentication for the\
server plugin _mysql\_native\_password_. This is the default authentication\
plugin used by both MariaDB and MySQL.

### Authenticator options

The following settings may be given in the _authenticator\_options_ of the\
listener.

#### `log_password_mismatch`

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: No
* Default: `false`

The service setting _log\_auth\_warnings_ must\
also be enabled for this setting to have effect. When both settings are enabled,\
password hashes are logged if a client gives a wrong password. This feature may\
be useful when diagnosing authentication issues. It should only be enabled on a\
secure system as the logging of password hashes may be a security risk.

#### `cache_dir`

Deprecated and ignored.

#### `inject_service_user`

Deprecated and ignored.

CC BY-SA / Gnu FDL
