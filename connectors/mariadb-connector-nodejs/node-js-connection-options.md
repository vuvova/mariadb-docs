# Node.js Connection Options

- [Essential options](#essential-option)
- [Support for big integer](#support-for-big-integer)
- [Ssl](#ssl)
    - [Configuration](#configuration)
    - [Certificate validation](#certificate-validation)
    - [One-way SSL authentication](#one-way-ssl-authentication)
    - [Two-way SSL authentication](#two-way-ssl-authentication)
- [Other options](#other-options)
- [F.A.Q.](#faq)

## Essential Options

|                 option | description                                                                                                                                                                                                                                                              |   type    |   default   | 
|-----------------------:|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------:|:-----------:| 
|               **user** | User to access database                                                                                                                                                                                                                                                  | *string*  |
|           **password** | User password                                                                                                                                                                                                                                                            | *string*  |
|               **host** | IP address or DNS of database server. *Not used when using the `socketPath` option*                                                                                                                                                                                      | *string*  | "localhost" |  
|               **port** | Database server port number                                                                                                                                                                                                                                              | *integer* |    3306     |
|           **database** | Default database to use when establishing the connection                                                                                                                                                                                                                 | *string*  |
|         **socketPath** | Permit connecting to the database via Unix domain socket or named pipe, if the server allows it                                                                                                                                                                          | *string*  |
|           **compress** | Compress exchanges with database using gzip.  This can give you better performance when accessing a database in a different location.                                                                                                                                    | *boolean* |    false    |  
|     **connectTimeout** | Connection timeout in milliseconds (default changed from 10000 to 1000 in 2.5.6)                                                                                                                                                                                         | *integer* |    1000     |
|      **socketTimeout** | Socket timeout in milliseconds after the connection is established                                                                                                                                                                                                       | *integer* |      0      |
|        **rowsAsArray** | Return result-sets as array, rather than a JSON object. This is a faster way to get results.  For more information, see the [Promise](../README.md#querysql-values---promise) and [Callback](callback-api.md#querysql-values-callback---emoitter) query implementations. | *boolean* |    false    |
|   **maxAllowedPacket** | permit to indicate server global variable [max_allowed_packet](https://mariadb.com/docs/server/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables/#max_allowed_packet) value to ensure efficient batching. default is 4Mb. see [batch documentation](./batch.md)                                  | *integer* |   4196304   |
|   **insertIdAsNumber** | Whether the query should return last insert id from INSERT/UPDATE command as BigInt or Number. default return BigInt                                                                                                                                                     | *boolean* |    false    |
|    **decimalAsNumber** | Whether the query should return decimal as Number. If enable, this might return approximate values.                                                                                                                                                                      | *boolean* |    false    |
|     **bigIntAsNumber** | Whether the query should return BigInt data type as Number. If enable, this might return approximate values.                                                                                                                                                             | *boolean* |    false    |
|             **logger** | Permit custom logger configuration. For more information, see the [`logger` option](#logger) documentation.                                                                                                                                                              |  *mixed*  |
| **prepareCacheLength** | Define prepare LRU cache length. 0 means no cache                                                                                                                                                                                                                        |   *int*   |     256     |
|         **fullResult** | indicate if user wants to retrieve individual batch results (in order to retrieve generated ids). This might change the performance of batching if set, depending on server version: if set, for server 11.5.1 and above, bulk will be use, pipelining if not        | *boolean* |             |



### JSON or String configuration

Options can be set as a JSON Object, or a using a String.

String format is :

`mariadb://[<user>[:<password>]@]<host>[:<port>]/[<db>[?<opt1>=<value1>[&<optx>=<valuex>]]]`

example:
```javascript
const mariadb = require('mariadb');
//passing argument as JSON object
mariadb.createConnection({ 
    user: 'root', 
    password: 'pass', 
    port: 3307,
    database: 'db',
    metaAsArray: false,
    ssl: true,
    dateStrings: true  
  });

//passing argument as String
mariadb.createConnection('mariadb://root:pass@localhost:3307/db?metaAsArray=false&ssl=true&dateStrings=true');
```
## logger

Driver permits mapping the logs to an external logger.
There are 4 caller functions:
* network(string): called for each network exchanges.
* query(string): called for each command
* error(Error): called for each error.
* warning(string): called for each warning (configuration warning, leak message), default to console.log if not set.

if setting one function, function will be used for all loggers.
(i.e., logger: console.log  ===  logger: { network: console.log, query: console.log, error: console.log})

2 options defined what will be logged : `debugLen` and `logParam`.
query and network logs are truncated to `debugLen` length (default to 256).
truncated trace finish by '...': example :
```javascript
QUERY: insert into bigParameterInt8 values(?, ?) - parameters:['0000000...]
==> conn:57 Query(0,1031)
+--------------------------------------------------+
|  0  1  2  3  4  5  6  7   8  9  a  b  c  d  e  f |
+--------------------------------------------------+------------------+
| 03 04 00 00 03 69 6E 73  65 72 74 20 69 6E 74 6F | .....insert into |
| 20 62 69 67 50 61 72 61  6D 65 74 65 72 49 6E 74 |  bigParameterInt |
| 38 20 76 61 6C 75 65 73  28 27 30 30 30 30 30 30 | 8 values('000000 |
| 30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30 | 0000000000000000 |...
+--------------------------------------------------+------------------+
```

**Example:**

```js
const mariadb = require('mariadb');
const winston = require('winston');

const logger = winston.createLogger({
  level: 'info',
  transports: [
    // - Write all logs with level `error` and below to `error.log`
    // - Write all logs with level `info` and below to `combined.log`
    new winston.transports.Console({ filename: 'error.log', level: 'error' }),
    new winston.transports.Console({ filename: 'combined.log' })
  ]
});

const pool = mariadb.createPool({
  host: 'mydb.com',
  user:'myUser',
  password: 'myPwd',
  logger: {
    network: (msg) => logger.silly(msg),
    query: (msg) => logger.info(msg),
    error: (err) => logger.error(err),
  }
});
```

## SSL

The Connector can encrypt data during transfer using the Transport Layer Security (TLS) protocol.  TLS/SSL allows for transfer encryption, and can optionally use identity validation for the server and client.

> The term SSL (Secure Sockets Layer) is often used interchangeably with TLS, although strictly-speaking the SSL protocol is the predecessor of TLS, and is not implemented as it is now considered insecure.

There are two different kinds of SSL authentication:

- **One-Way SSL Authentication:** The client verifies the certificate of the server.  This allows you to encrypt all exchanges and make sure that you are connecting to the expected server, (to avoid a man-in-the-middle attack).
- **Two-Way SSL Authentication** The client verifies the certificate of the server, the server verifies the certificate of the client.  This is also called mutual authentication or client authentication.  When using this system, the client also requires a dedicated certificate.


### Server Configuration

In order to use SSL, you need to ensure that the MariaDB Server is correctly configured.  You can determine this using the `have_ssl` system variable.

```sql
SHOW VARIABLES LIKE 'have_ssl';

+---------------+----------+
| Variable_name | Value    |
+---------------+----------+
| have_ssl      | DISABLED |
+---------------+----------+
```

A value of `NO` indicates that MariaDB was compiled without support for TLS.  `DISABLED` means that it was compiled with TLS support, but it's currently turned off.  In order to use SSL with the Connector, the server must return `YES`, indicating that TLS support is available and turned on.
For more information, see the [MariaDB Server](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/securing-mariadb-encryption/data-in-transit-encryption) documentation.


### User Configuration

Enabling the [ssl option](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/starting-and-stopping-mariadb/mariadbd-options) on the server, the Connector uses one-way SSL authentication to connect to the server. Additionally, it's recommended that you also configure your users to connect through SSL. This ensures that their accounts can only be used with an SSL connection.

For [GRANT statements](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements-and-structure/sql-statements/account-management-sql-commands/grant), use the [REQUIRE SSL](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements-and-structure/sql-statements/account-management-sql-commands/grant#per-account-ssltls-options) option for one-way SSL authentication and the [REQUIRE X509](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements-and-structure/sql-statements/account-management-sql-commands/grant#per-account-ssltls-options) option for two-way SSL authentication. For more information, see the [CREATE USER](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements-and-structure/sql-statements/account-management-sql-commands/create-user) documentation.

```sql
CREATE USER 'johnSmith'@'%' IDENTIFIED BY PASSWORD('passwd');
GRANT ALL ON company.* TO 'johnSmith'@'%' REQUIRE SSL;
```

Now when this user attempts to connect to MariaDB without SSL, the server rejects the connection.



### Configuration

* `ssl`: boolean/JSON object.

JSON object:

|option|description|type|default| 
|---:|---|:---:|:---:| 
|**checkServerIdentity**| `function(servername, cert)` to replace SNI default function| *Function*|
|**minDHSize**| Minimum size of the DH parameter in bits to accept a TLS connection | *number*|1024|
|**pfx**| Optional PFX or PKCS12 encoded private key and certificate chain. Encrypted PFX will be decrypted with `passphrase` if provided| *string / string[] / Buffer / Buffer[] / *Object[]*|
|**key**| Optional private keys in PEM format. Encrypted keys are decrypted with `passphrase` if provided| *string / string[] / *Buffer* / *Buffer[]* / *Object[]*|
|**passphrase**| Optional shared passphrase used for a single private key and/or a PFX| *string*|
|**cert**| Optional cert chains in PEM format. One cert chain should be provided per private key| *string / string[] / Buffer / Buffer[]*|
|**ca**| Optionally override the trusted CA certificates. Default is to trust the well-known CAs curated by Mozilla. For self-signed certificates, the certificate is its own CA, and must be provided| *string / string[] / Buffer / Buffer[]*|
|**ciphers**| Optional cipher suite specification, replacing the default| *string*|
|**honorCipherOrder**| Attempt to use the server's cipher suite preferences instead of the client's| *boolean*|
|**ecdhCurve**| A string describing a named curve or a colon separated list of curve NIDs or names, for example P-521:P-384:P-256, to use for ECDH key agreement, or false to disable ECDH. Set to auto to select the curve automatically| *string*|tls.DEFAULT_ECDH_CURVE|
|**clientCertEngine**| Optional name of an OpenSSL engine which can provide the client certificate| *string*|
|**crl**| Optional PEM formatted CRLs (Certificate Revocation Lists)| *string / string[] / Buffer / Buffer[]*|
|**dhparam**| Diffie Hellman parameters, required for Perfect Forward Secrecy| *string / Buffer*|
|**secureProtocol**| Optional SSL method to use, default is "SSLv23_method" | *string*|

The Connector uses the Node.js implementation of TLS.  For more information, see the [Node.js TLS API](https://nodejs.org/api/tls.html#tls_tls_connect_options_callback) documentation.


### Certificate Validation

#### Trusted CA

By default, Node.js trusts the well-known root Certificate Authorities (CA), based on Mozilla.  For a complete list, (including the popular and free Let's Encrypt), see the [CA Certificate List](https://ccadb-public.secure.force.com/mozilla/IncludedCACertificateReport).

When using a certificate signed with a certificate chain from a root CA known to Node.js, the only configuration you need to do is enable the `ssl` option.


#### Certificate Chain Validation

A certificate chain is a list of certificates that were issued from the same Certification Authority hierarchy.
In order for any certificate to be validated, all certificates in the chain have to be validated.

In cases where the Connector does not trust intermediate or root certificates, the Connector rejects the connection and issues an error.


#### Hostname Verification (SNI)

Certificates can provide hostname verification to the driver.
By default, this is done against the certificate's `subjectAlternativeName` DNS name field.


### One-way SSL Authentication

When the server certificate is signed using the certificate chain that uses a root CA known in the JavaScript trust store, setting the `ssl` option enables one-way SSL authentication.


For example,

```js
const mariadb = require('mariadb');
mariadb
 .createConnection({
   host: 'myHost.com', 
   ssl: true, 
   user: 'myUser', 
   password:'MyPwd', 
   database:'db_name'
 }).then(conn => {})
```
Since MariaDB 11.4, server supports ["zero configuration ssl"](https://mariadb.org/mission-impossible-zero-configuration-ssl/) that permits avoiding having to set any other information than `ssl: true`.

Previously to this version or using non-MariaDB server, when the server uses a self-signed certificate or uses an intermediate certificate, there are two different possibilities:

In non-production environments, you can tell the Connector to trust all certificates by setting `rejectUnauthorized` to `false`.  Do **NOT** use this in production.

```js
//connecting
mariadb
 .createConnection({
   host: 'myHost.com', 
   ssl: {
	 rejectUnauthorized: false
   }, 
   user: 'myUser', 
   password:'MyPwd', 
 }).then(conn => {})
```

A more secure alternative is to provide the certificate chain to the Connector.

```js
const fs = require("fs");
const mariadb = require('mariadb');

//reading certificates from file
const serverCert = [fs.readFileSync("server.pem", "utf8")];

//connecting
mariadb
 .createConnection({
   user: "myUser",
   host: "myHost.com",
   ssl: {
	 ca: serverCert
   }
 }).then(conn => {})
```


#### Using Specific TLS Protocols or Ciphers

In situations where you don't like the default TLS protocol or cipher or where you would like to use a specific version, you force he Connector to use the one you want using the `secureProtocol` and `cipher` options.

For instance, say you want to connect using TLS version 1.2:

```js
//connecting
mariadb
 .createConnection({ 
   user:"myUser", 
   host: "myHost.com",
   ssl: {
	 ca: serverCert,
	 secureProtocol: "TLSv1_2_method",
	 ciphers:
	   "ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256"        
   }
 }).then(conn => {})
```

For more information on what's available, see [possible protocol](https://www.openssl.org/docs/man1.0.2/ssl/ssl.html#DEALING-WITH-PROTOCOL-METHODS) values.


### Two-way SSL Authentication

Mutual SSL authentication or certificate-based mutual authentication refers to two parties authenticating each other by verifying the provided digital certificates.  This allows both parties to be assured of the other's identity.  In order to use mutual authentication, you must set the `REQUIRE X509` option in the `GRANT` statement.  For instance,

```sql
GRANT ALL ON company.* TO 'johnSmith'@'%' REQUIRE X509;
```

This option causes the server to ask the Connector for a client certificate.  **If the user is not set with `REQUIRE X509`, the server defaults to one-way authentication**

When using mutual authentication, you need a certificate, (and its related private key), for the Connector as well as the server.  If the Connector doesn't provide a certificate and the user is set to `REQUIRE X509`, the server returns a basic `Access denied for user` message.

In the event that you would like to see how users are defined, you can find this information by querying the `mysql.user` table on the server.  For instance, say you wanted information on the `johnSmith` user.

```sql
SELECT ssl_type, ssl_cipher, x509_subject 
FROM mysql.user
WHERE USER = 'johnSmith';
```

You can test it by creating a user with `REQUIRE X509` for testing:

```sql
CREATE USER 'X509testUser'@'%';
GRANT ALL PRIVILEGES ON *.* TO 'X509testUser'@'%' REQUIRE X509;
```

Then use its credentials in your application:

```js
const fs = require("fs");
const mariadb = require('mariadb');

//reading certificates from file
const serverCert = [fs.readFileSync("server.pem", "utf8")];
const clientKey = [fs.readFileSync("client.key", "utf8")];
const clientCert = [fs.readFileSync("client.pem", "utf8")];

//connecting
mariadb
 .createConnection({ 
   user:"X509testUser", 
   host: "mariadb.example.com",
   ssl: {
	 ca: serverCert,
	 cert: clientCert,
	 key: clientKey
   }
 }).then(conn => {})
```

#### Using Keystores

Keystores allow you to store private keys and certificate chains encrypted with a password to file.   For instance, using OpenSSL you can generate a keystore using PKCS12 format:

```bash
openssl pkcs12 \
	-export \
	-in "${clientCertFile}" \
	-inkey "${clientKeyFile}" \
	-out "${keystoreFile}" \
	-name "mariadbAlias" \
	-passout pass:kspass
```

You can then use the keystore in your application:

```js
const fs = require("fs");
const mariadb = require('mariadb');

//reading certificates from file (keystore must be read as binary)
const serverCert = fs.readFileSync("server.pem", "utf8");
const clientKeystore = fs.readFileSync("keystore.p12");

//connecting
mariadb.createConnection({ 
 user:"X509testUser", 
 host: "mariadb.example.com",
 ssl: {
   ca: serverCert,
   pfx: clientKeystore,
   passphrase: "kspass"
 }
}).then(conn => {});
```

## Other Options

|option| description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |      type      |      default       | 
|---:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------:|:------------------:| 
| **charset** | Protocol character set used with the server. Connection collation will be the [default collation](https://github.com/mariadb-corporation/mariadb-connector-nodejs/blob/master/lib/const/collations.js#L372) associated with charset. It's mainly used for micro-optimizations.  The default is often sufficient.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |    *string*    |      UTF8MB4       | 
| **collation** | (used in replacement of charset) Permit to defined collation used for connection. This will defined the charset encoding used for exchanges with database and defines the order used when comparing strings. It's mainly used for micro-optimizations                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |    *string*    | UTF8MB4_UNICODE_CI | 
| **dateStrings** | Whether to retrieve dates as strings or as `Date` objects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |   *boolean*    |       false        | 
| **debug** | Logs all exchanges with the server.  Displays in hexa.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |   *boolean*    |       false        | 
| **debugLen** | String length of logged message / error or trace                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |     *int*      |        256         | 
| **logParam** | indicate if parameters must be logged by query logger.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |   *boolean*    |       false        |
| **foundRows** | When enabled, the update number corresponds to update rows.  When disabled, it indicates the real rows changed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |   *boolean*    |        true        |
| **multipleStatements** | Allows you to issue several SQL statements in a single `quer()` call. (That is, `INSERT INTO a VALUES('b'); INSERT INTO c VALUES('d');`).  <br/><br/>This may be a **security risk** as it allows for SQL Injection attacks.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |   *boolean*    |       false        |
| **namedPlaceholders** | Allows the use of named placeholders.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |   *boolean*    |       false        |
| **permitLocalInfile** | Allows the use of `LOAD DATA INFILE` statements.<br/><br/>Loading data from a file from the client may be a security issue, as a man-in-the-middle proxy server can change the actual file the server loads.  Being able to execute a query on the client gives you access to files on the client.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |   *boolean*    |       false        |
| **timezone** | Forces use of the indicated timezone, rather than the current Node.js timezone. This has to be set when database timezone differ from Node.js timezone. Possible values are [IANA time zone](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) (ex: 'America/New_York')                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |    *string*    |
| **nestTables** | Presents result-sets by table to avoid results with colliding fields.  See the `query()` description for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |   *boolean*    |       false        |
| **pipelining** | Sends queries one by one without waiting on the results of the previous entry.  For more information, see [Pipelining](/documentation/pipelining.md)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |   *boolean*    |        true        |
| **trace** | Adds the stack trace at the time of query creation to the error stack trace, making it easier to identify the  part of the code that issued the query.  Note: This feature is disabled by default due to the performance cost of stack creation.  Only turn it on when you need to debug issues.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |   *boolean*    |       false        |
| **typeCast** | Allows you to cast result types.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |   *function*   |
| **connectAttributes** | Sends information, (client name, version, operating system, Node.js version, and so on) to the [Performance Schema](https://mariadb.com/docs/server/reference/sql-statements/administrative-sql-statements/system-tables/performance-schema/performance-schema-tables/performance-schema-session_connect_attrs-table). When enabled, the Connector sends JSON attributes in addition to the defaults.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | *boolean/json* |       false        |
| **metaAsArray** | Compatibility option, causes Promise to return an array object, `[rows, metadata]` rather than the rows as JSON objects with a `meta` property.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |   *boolean*    |       false        |
| **permitSetMultiParamEntries** | Compatibility option to permit setting multiple value by a JSON object to replace one question mark. key values will replace the question mark with format like `key1`=val,`key2`='val2'. Since it doesn't respect the usual prepared statement format that one value is for one question mark, this can lead to incomprehension, even if badly use to possible injection. this only works using `query` function (not compatible with `batch` and `execute` functions)                                                                                                                                                                                                                                                                                                                         |   *boolean*    |       false        |
| **sessionVariables** | Permit to set session variables when connecting. Example: sessionVariables:{'idle_transaction_timeout':10000}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |     *json*     |
| **initSql** | When a connection is established, permit to execute commands before using connection                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |    *string     |       array*       |
| **bulk** | disabled bulk command in batch                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |   *boolean*    |
| **permitConnectionWhenExpired** | Permit a user with expired password to connect. Only possible operation in this case will be to change password ('SET PASSWORD=PASSWORD('XXX')')                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |   *boolean*    |       false        |
| **forceVersionCheck** | Force server version check by explicitly using SELECT VERSION(), not relying on server initial packet.<br/><i><small>Since version 2.2.0</small></i>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |   *boolean*    |       false        |
| **checkDuplicate** | Indicate to throw an exception if result-set will not contain some data due to having duplicate identifier. <br/>JSON cannot have multiple identical key, so query like `SELECT 1 as i, 2 as i` cannot result in { i:1, i:2 }, 'i:1' would be skipped. <br/>When `checkDuplicate` is enable (default) driver will throw an error if some data are skipped. Duplication error can be avoided by multiple ways, like using unique aliases or using options [`rowsAsArray`](https://github.com/mariadb-corporation/mariadb-connector-nodejs/blob/master/documentation/promise-api.md#rowsasarray) / [`nestTables`](https://github.com/mariadb-corporation/mariadb-connector-nodejs/blob/master/documentation/promise-api.md#nestTables) for example <br/><i><small>Since version 2.3.0</small></i> |   *boolean*    |        true        |
| **arrayParenthesis** | Indicate if array are included in parenthesis. This option permit compatibility with version < 2.5                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |   *boolean*    |       false        |
| **autoJsonMap** | indicate if JSON fields for MariaDB server 10.5.2+ results in JSON format (or String if disabled)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |   *boolean*    |        true        |
| **jsonStrings** | force JSON fields as string (MySQL JSON field or MariaDB server 10.5.2+ results in JSON format). When set, autoJsonMap is forced to false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |   *boolean*    |       false        |
| **keepAliveDelay** | permit to enable socket keep alive, setting delay. 0 means not enabled. Keep in mind that this don't reset server [@@wait_timeout](https://mariadb.com/docs/server/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables/#wait_timeout) (use pool option idleTimeout for that). in ms. For mysql2 compatibility, setting enableKeepAlive and keepAliveInitialDelay alias is permitted. i.e. enableKeepAlive=true&keepAliveInitialDelay=1000 corresponds to setting keepAliveDelay=1000 directly                                                                                                                                                                                                                                                                                                                             |     *int*      |                    |
| **rsaPublicKey** | Indicate path/content to MySQL server RSA public key. use requires Node.js v11.6+                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |    *string*    |                    |
| **cachingRsaPublicKey** | Indicate path/content to MySQL server caching RSA public key. use requires Node.js v11.6+                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |    *string*    |                    |
| **allowPublicKeyRetrieval** | Indicate that if `rsaPublicKey` or `cachingRsaPublicKey` public key are not provided, if client can ask server to send public key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |   *boolean*    |       false        |
| **restrictedAuth** | if set, restrict authentication plugin to secure list. Default provided plugins are mysql_native_password, mysql_clear_password, client_ed25519, dialog, sha256_password and caching_sha2_password                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |     *Array     |      String*       | |
| **supportBigNumbers** | (deprecated) DECIMAL/BIGINT data type will be returned as number if in safe integer range, as string if not.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |   *boolean*    |       false        |
| **bigNumberStrings** | (deprecated) if set with `supportBigNumbers` DECIMAL/BIGINT data type will be returned as string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |   *boolean*    |       false        |
| **stream** | permits to set a function with parameter to set stream (since 3.0)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |   *function*   |                    |
| **bitOneIsBoolean** | return BIT(1) values as boolean                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |   *boolean*    |        true        |
| **checkNumberRange** | when used in conjunction of decimalAsNumber, insertIdAsNumber or bigIntAsNumber, if BigInt conversion to number is not exact, connector will throw an error (since 3.0.1)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |   *function*   |                    |
| **metaEnumerable** | make resultset meta property enumerable (since 3.0.2)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |   *boolean*    |       false        |
| **infileStreamFactory** | When LOAD LOCAL command executed, permit to set a callback function of type (filepath?: string) => stream.Readable. Connector will then not send file from LOAD LOCAL, but Readable content. This can permit to set extra validation of file path for example.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |   *function*   |                    |

### SSH tunnel

In some cases, the server is only available through an SSH tunnel.
(This is, of course, not a recommended solution for production)


The option `stream` permit defined a tunnel. stream function has a callback (optional parameters: error, stream).

Example using `tunnel-ssh`:

```js
const conn = await mariadb.createConnection({
        user: 'myUser',
        password: 'mYpwd',
        port: 27000,
        stream: (cb) => {
          const tunnel = require('tunnel-ssh');
          tunnel(
            {
              // remote connection ssh info
              username: 'root',
              host: '157.230.123.7',
              port: 22,
              privateKey: fs.readFileSync('./pop_key.ppk'),
              // database (here on ssh server)
              dstHost: '127.0.0.1',
              dstPort: 3306,
              // local interface
              localHost: '127.0.0.1',
              localPort: 27000
            },
            cb
          );
        }
      });
```


## F.A.Q.

#### error Hostname/IP doesn't match certificate's alt-names

Clients verify certificate SAN (subject alternative names) and CN to ensure that the certificate corresponds to the hostname.  If the certificate's SAN/CN does not correspond to the `host` option, it returns an error such as:

```
Hostname/IP doesn't match certificate's altnames: "Host: other.example.com. is not cert's CN: mariadb.example.com"
```
To fix this, correct the `host` value to correspond to the host identified in the certificate.

####  routines:ssl_choose_client_version:unsupported protocol

Since Node.js 12, the minimum TLS version is set to 1.2.
MariaDB server can be built with many different SSL libraries, the old version supporting only TLS up to 1.1.  
The error "1976:error:1425F102:SSL routines:ssl_choose_client_version:unsupported protocol" can occur if MariaDB SSL implementation doesn't support TLSv1.2.
This can be solved by :
- Server side: update MariaDB to a recent version
- Client side: permit a lesser version with "tls.DEFAULT_MIN_VERSION = 'TLSv1.1';" or with connection configuration: using option `ssl: { secureProtocol: 'TLSv1_1_method' }'


{% @marketo/form formId="4316" %}
